会飞的梧鼠
2压10bit里面的预设是最早的，目前本人已经基本不用，保留他的目的是为了参考里面的滤镜，不过直接使用也是没什么问题的，质量偏低了一些。最新可以使用 2压 HEVC 10bit x265 中的预设文件，但只保留了默认的去块和锐化滤镜

推荐动漫选20起步，真人影视和3D作品选22起步，综艺选择26起步，然后自己设定一个最大码率，超过这个码率可以使用更低质量的预设尝试，或者直接使用码率模式，这样兼顾了质量和体积

210的意思是2压 10bit
S代表“标准动态范围SDR”
反代表反交错处理，用于处理隔行扫描的视频
滤反代表使用yadif滤镜反交错
实反代表直接添加参数反交错
性能更好，但只能处理真正的隔行扫描视频，滤反可以处理带有隔行扫描缺陷的逐行视频

块 代表去块滤镜
降 代表降噪滤镜
带 代表去色带滤镜

锐化和块对于软件编码基本都是标配，硬件编码默认什么都没有，为了不影响速度

FMP4 代表流动的MP4，即添加了一个参数使其更适合网络在线播放
压缩效率：
MPEG4<H264<HVEC<AV1 AV1需要的时间大概是H265的几十倍
HVEC(AMF,NVENC,QSV)
分别代表着使用A卡，N卡，核显进行压缩
shanaEncoder的视频量化器三个选项
1.比特率
几乎从头到尾使用一样的比特率，缺点：画面变化大的地方比特率太小，画面变化小的时候比特率又太大。优点：文件大小一定。
2.量化器
一般量化器给到18-28，注意：越小代表视频质量越好。小于18可以理解成为无损的。
3000固定码率大小是：2.44G，量化器20大小是2.05G，量化器28大小是：879MB，量化器18大小2.80G，量化器24大小1.29G。量化器19大小2.37G。我们可以理解为量化器18-19大约等于3000固定码率。使用强制128的音频会把视频大小从2.8G降低到2.7G，量化器18。量化器19的话，如果强制128的音频大小会是2.27G。
3K的码率大小：2.44G：相对0.17
18量化器2.7G：相对0.43
19量化器2.27G：相对0
###计算得出3K的码率换算成量化器就是18.395。
1950码率大小是：1.64G
2500码率大小是：2.07G
28的量化器大小是774MB
28量化器,774
18,2700
19,2270
每增加一级，减少192.6MB。但其实不是线性的
20，1950
19,2270
2500,2070
也就是说2500码率相当于量化器的19-20。相当于19.375的量化器
22,1470
21的量化器结果还未知敬请期待,1650MB。得出结论21量化器基本就是1950码率
21,1950
18.395,3000
19.375,2500
试一试不加时间戳大小多大
3.质量
使用质量选项卡的几次尝试全部大于4G。
相当于量化器的优化版本。体积比量化器低，质量还比量化器好。
关键帧一般给5-15。10就很好。
裁剪就是让画面没有黑边。填充就是让画面有黑边。
尺寸一般常规写法：1280X720
我们这里第一个参数可以不写1280而是写-2（必须要是偶数）。代表着我们给720的宽他可以自动计算出1280的高。
恒定帧速率编码 最好勾上。
编码选项卡里面 预设选veryfast下面的，不要选择比这个快的。调整推荐ssim。模糊/锐化0.06
你能吃多少，给你多少碗饭。一般这个值设定在18-28之间。
压缩时间成反比
shanaencoder再次学习。拼接就是合并视频。