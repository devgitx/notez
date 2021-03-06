
# 临时记录


#### 睡眠时间型判别方式

学术界里广泛使用慕尼黑时间型问卷（Munich ChronoType Questionnaire, MCTQ）来判定个体的时间型。这个问卷挺复杂的，所以姚脑师这里就把关键的部分翻译出来给大家做时间型的判断。

时间型的判断是根据你工作日睡眠的长度和非工作日（周末）睡眠的长度，来计算睡眠周期的中点（Mid-Sleep）。

需要注意的是非工作日不可以使用闹钟，测试的必须是睡到自然醒的长度。我们可以用现在的手机或是可戴式手表来检测睡眠的长度，然后求自己工作日和非工作日睡眠的平均长度。

我们来看怎么计算自己的时间型（请使用 24 小时格式来计算）：

睡眠长度 = 起床时间 - 入睡时间（不是上床时间）

如果你的工作日睡眠长度 ≥ 非工作日睡眠长度，时间型 = 非工作日入睡时间 + 非工作日睡眠长度 / 2;

如果你的工作日睡眠长度 < 非工作日睡眠长度，时间型 = 非工作日入睡时间 + 非工作日睡眠长度 / 2 - （非工作日的睡眠长度 - 工作日的睡眠长度）/2

我们来看个例子。假设你工作日都是 00:00 入睡，06:30 起床，你的工作日睡眠长度就是 06:30。到了周末，你 01:00 才睡，到第二天 09:00 才起床，那么你的非工作日睡眠长度就是 08:00。

因为你的工作日睡眠长度要短于非工作日的睡眠长度，那我们就要用第二个公式。时间型 = 01:00 + 08:00/2 - (08:00 - 06:30)/2 = 05:00 - 00:45 = 04:15。

也就是说，你自然睡眠周期的中点是早上 4 点 15 分。那我们看下图的时间型分布。04:15 落在从右至左的第三个柱上（4 那个柱上），属于轻度夜猫型，有 23%的人属于这种类型。

如果没有工作日和非工作日的作息切换，你的自然睡眠周期（按 8 小时睡眠长度）应该是 00:15 - 8:15。

### 如何在mac上格式化ext3、ext4

1. 确认已安装安装 Homebrew，用 `brew install e2fsprogs` 
2. 插上 U盘，执行 `diskutil list`, 在执行结果中找到 U盘盘符，我这里是 /dev/disk2s1
3. 卸载 U盘并将其格式化为 ext2/3/4 格式
```
diskutil unmountdisk /dev/disk2s1
sudo $(brew --prefix e2fsprogs)/sbin/mkfs.ext3 /dev/disk2s1
```
4. 按提示操作即可。格式化完成就能直接拔掉 U盘了.