DIA：duration of insulin action  胰岛素作用持续时间
ISF：insulin sensitivity factor  胰岛素敏感系数   [mg/dL/U/m，即每分钟每单位胰岛素血糖的变化量]
IOB：insulin on board  整装待发的胰岛素/装配好的胰岛素
ICR：insulin to carb (IC) ratio  胰岛素碳水化合系数
BGI：BG Impact= IOB * ISF  血糖影响度     IOB（10U）、ISF（mg/dL/5m）


net IOB：it’s IOB that takes into account any basal adjustments in addition to bolus insulin. so any basal ABOVE your usual will be positive IOB and any BELOW usual will contribute negative IOB。

净整装待发的胰岛素：指的是除了大剂量胰岛素之外的已经输注的任意调整的临时基础量。

There are two types of curves.
有两种类型的曲线

The IOB curve tracks insulin on board, the insulin that has been injected but hasn't taken effect yet.
IOB曲线是指已经注射了的但是还没有起效的胰岛素曲线.

The insulin activity curve tracks how much insulin is taking effect right now. That is the derivative of the IOB curve, mathematically。(The slope of the IOB curve at that point.)
活性胰岛素曲线是指监测有多少胰岛素现在已经起效的。这个是IOB曲线求导得来的。（这个是IOB曲线在某一个点上的斜率）

oref0: The open reference implementation of the OpenAPS reference design.



示例：用户当前血糖值：a；目标血糖值：b；血糖由a到b的时间为：t（小时为单位）；摄入等值碳水化合物克数：x；注射胰岛素剂量：y；胰岛素敏感系数：ISF（单位小时内）；碳水化合物系数：ICR

消耗摄入碳水化合物所需胰岛素：X*ICR
降血糖到目标值所需胰岛素剂量：（a-b）/ISF

需要注射胰岛素剂量：y=（a-b）/ISF - X*ICR


OpenAPS使用胰岛素泵大剂量以及临时基础量的历史值，结合胰岛素泵里胰岛素的作用时长和公开的IOB曲线，去计算当前的IOB净值。（目前来说，当计算输入输出数据的时候，胰岛素泵仅仅包含剂量信息：更加精确的输入输出计算包含临时剂量和常规计划中的基础率） 如果当前没有大剂量被管理，OpenAPS能够使用当前的动态血糖仪数据去计算最终的血糖预测值，可以使用这个简单的剂量计算公式：当前血糖值-（胰岛素敏感系数*输入剂量）=预测的血糖值。

如果当前血糖值低于设定阈值（默认低于目标血糖管理区间1.67mmol/L），OpenAPS进入低血糖暂停模式，并且简单地在30分钟内持续注射临时剂量到0直到血糖值不再上升中。另外，OpenAPS决定预测的血糖值是否高于或者低于目标血糖区间，并且备注是否动态血糖值当前比预期是上升或下降多少。然后决定适当地执行以下过程：
1. 如果血糖上升但最终血糖值是低于目标，则取消任何临时基础量；
2. 否则，如果血糖值正在下降中但是最终的血糖值是高于目标区间，则取消任何临时基础量；
3. 否则，如果最终的血糖值高于目标区间：a.计算30分钟内需要让最终血糖值低于目标区间的临时基础量；b. 如果需要的的临时基础量小于现有的基础量，确定最新的低临时基础量。如果需要0基础量的时间超过30分钟，则延长0基础量的时间到30m；

最大基础率是设置在胰岛素泵里面，但是在OpenAPS上面为了安全的考虑，将设置一个比较低的最大基础率，如果需要的话。最小基础率的设置如下：
1. 胰岛素泵最大临时基础率；
2. 3*日最大计划基础率；
3. 4*当前设置好的基础率；

这个能确保患者总可以使用OpenAPS方便地通过食用快速作用的碳水化合物从过度的胰岛素注射中恢复过来。


调整意外的血糖偏离

以上的算法对于简单安全的OpenAPS的实施是足够的，并已成功测试了几十个用户数年以上的组合使用。但是在血糖上升或者下降的一些以外情况，或居高不下时，我们发现，考虑到血糖上升/下降率与基于胰岛素活性的预期值有多大的偏差有关系的，这也是很有用的。这让更多的高级OpenAPS实施来快速应对血糖开始上升或下降超过预期值，并且让系统能够在血糖居高不下或者下降远低于预期（血糖值几乎呈现高值水平直线）时，持续地执行高临时基础量。

为了计算这个偏离，OpenAPS首先计算一个术语叫做“血糖影响”或者BGI，我们这样简单地进行计算：BGI=当前的胰岛素活性（IOB的一阶导数）*胰岛素敏感系数。当用mg/dL/5m为单位表达时，这个代表血糖升高或下降的度数，能够直接和最近两次血糖读数的差值进行比较，或者和最近15分钟的平均增量值进行比较。 为了计算偏差，OpenAPS确实做了这样的比较，动态15分钟的差值平均值和预测的血糖值。然后应用该偏差的调整最终血糖预测。这个是基于这样的假设，如果血糖在过去的15分钟上升或下降超过预期值，这个趋势很有可能在下一个15到30分钟持续，持续的偏差大小大致相当于在过去的15分钟内所看到的。在未来的openaps实现可能会想出比这种更好的预测算法，但实际使用至今，该算法已经简单工作很好有几个月了。

此外在调整最终血糖预测值时候，上面BGI的计算仍然被用在高级OpenAPS执行上，用来让高临时基础量来持续的输注，如果血糖掉的比预期很慢（小于1/2BGI），并且同样地适用于设置低临时基础量，当血糖在上升很慢超过预期或者下降太快超过预期时。

剂量间歇

通过调整血糖偏差如上所述，高级OpenAPS实施能够避免当血糖上升或者饭后居高不下时的低临时基础量输注，甚至能够避免进食被消化后或进食量没有被告知系统。此外，OpenAPS能够避免当血糖还没有开始上升时低临时基础量来抵消一顿进餐的输注或预输注。为了完成这个，高级OpenAPS实施需要申请一个“剂量间歇”，这个会让OpenAPS系统很快放手让用户自己去注射大剂量，并且当血糖下降低于低血糖阈值，上升超过预期，或者饭后血糖居高不下，或者血糖开始快速下降超过预期的时候重新代替用户控制系统，这样的结果就是，用户能够简单方便适当地注射自己的餐时大剂量，并且那样的话，OpenAPS将在必要的时候，等待并接手基础量的调整来让血糖回到正常的血糖区间在每个用餐结束后。

剂量间歇是OpenAPS通过监测大剂量的活性胰岛素（基于用户的胰岛素半衰期）依据净输注的活性胰岛素量，并且重新增加了大剂量活性胰岛素的血糖影响（附加一个小倍数）当决定是否设置一个低临时基础率的时候。如果“间歇期“血糖高过血糖目标范围，那样OpenAPS将不再设置一个低临时基础率，甚至最终血糖比血糖目标区间低很多。这个结果在OpenAPS里面有效地在一个大剂量之后快速拓宽了目标血糖区间，然后再逐步地在接下来的1-2个小时逐渐缩窄目标区间直到恢复到正常水平。

因为大部分胰岛素泵不会计算净活性胰岛素量，而是仅仅使用大剂量来做计算，这个对于防止父母人为地通过大剂量计算器来过量使用大剂量是非常必要的一个附加的预防措施。这个是通过设置一个叫做“最大体内剩余胰岛素”来完成的，这个框架OpenAPS不会设置一个高的临时基础率来允许实际输注的IOB超过大剂量的IOB根据用户设置的数量。除非用户设置了OpenAPS，这个最大的IOB默认为0，这意味着OpenAPS将充当一个低血糖预测暂停系统，这样的话系统在血糖开始恢复后如果IOB是负值，将会使用高临时基础率，但是如果血糖是高的话将不确定使用高临时基础率。




here is the example, cod eis in javapublic class SensorSerialTest {
public static void main(String[] args) {
int tag1[] = {0xe0,0x07,0xa0,0x00,0x00,0x2a,0x97,0xe9};
char[] serial = serial(tag1);
System.err.println("output for tag1: "+new String(serial));
}
```java
private static char[] serial(int[] tagUID) {
    char snParts[] = {'0','1','2','3','4','5','6','7','8','9','A','C','D','E','F','G','H','J','K','L','M','N','P','Q','R','T','U','V','W','X','Y','Z'};
    if (tagUID == null || tagUID.length != 8) {
        return null;
    }
    int[] unsignedUid = new int[]{tagUID[5] & 0xFF, tagUID[4] & 0xFF, tagUID[3] & 0xFF, tagUID[2] & 0xFF, tagUID[1] & 0xFF, tagUID[0] & 0xFF};
    char result[] = new char[11];
    result[ 0] = '0'; //->unknown 
    result[ 1] = snParts[unsignedUid[0] >> 3];
    result[ 2] = snParts[((unsignedUid[0] & 7) << 2) | (unsignedUid[1] >> 6)];
    result[ 3] = snParts[(unsignedUid[1] >> 1) & 31];
    result[ 4] = snParts[((unsignedUid[1] & 1) << 4) | (unsignedUid[2] >> 4)];
    result[ 5] = snParts[((unsignedUid[2] & 15) << 1) | (unsignedUid[3] >> 7)];
    result[ 6] = snParts[(unsignedUid[3] >> 2) & 31];
    result[ 7] = snParts[((unsignedUid[3] & 3) << 3) | (unsignedUid[4] >> 5)];
    result[ 8] = snParts[unsignedUid[4] & 31];
    result[ 9] = snParts[unsignedUid[5] >> 3];
    result[10] = snParts[(unsignedUid[5] << 2) & 31];
    return result;
}
```


mongodb://backye:olijoolukmo9@ds115798.mlab.com:15798/fanqienightscout


echo 'MONGO_CONNECTION=mongodb://backye:olijoolukmo9@ds115798.mlab.com:15798/fanqienightscout' >> my.env 
echo 'MONGO_COLLECTION=entries' >> my.env
$env $(cat my.env) HOSTNAME=0.0.0.0  node  server.js
$env $(cat my.env) PORT=8080  node  server.js



 AR2 is a Nightscout feature for making 90th percentile confidence interval predictions of future BG values based solely on an autoregressive formula that uses only 2 BG values as its inputs.