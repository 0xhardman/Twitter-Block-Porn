## Twitter-Bock-Porn

受不了评论区黄推了? 打开[共享黑名单](https://twitter.com/i/lists/1677334530754248706), 用 [Twitter-Bock-Porn](https://greasyfork.org/zh-CN/scripts/470359-twitter-block-porn) 插件一键批量拉黑黄推, 手机上也能生效, 普通人拉黑受益的是自己, 大V拉黑受益的是所有人.

## 功能

- 共享黑名单, 一键拉黑所有黄推诈骗犯

  ![image](https://github.com/daymade/Twitter-Block-Porn/assets/4291901/b56331b2-368f-4716-b916-2654aefc9bca)

- 熟悉的小蓝鸟又飞回来了! 将 Logo 还原为 Twitter 原始的小鸟. 效果: 

  ![替换 logo](https://greasyfork.org/rails/active_storage/blobs/redirect/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBeC9BQVE9PSIsImV4cCI6bnVsbCwicHVyIjoiYmxvYl9pZCJ9fQ==--f05c18d96183f1c8de51bcd322b9dd476e555da0/F14jEjkWIAEg3wS.png?locale=zh-CN)


## 使用方式：
1. 打开脚本[主页](https://greasyfork.org/zh-CN/scripts/470359-twitter-block-porn), 安装脚本.

   <img width="547" alt="image" src="https://github.com/daymade/Twitter-Block-Porn/assets/4291901/15d98829-8615-4ef7-9fbf-c2297cac8b23">

3. 用电脑打开列表, 点击跳转到 [列表①](https://twitter.com/i/lists/1677334530754248706) [列表②](https://twitter.com/i/lists/1683810394287079426)，或者直接点击插件图标可以跳转到各个黑名单.

   <img width="256" alt="image" src="https://github.com/daymade/Twitter-Block-Porn/assets/4291901/2cc2baa9-e116-4d91-b8fa-6c5b1be887ac">
4. 在推特**列表**的页面, 点列表**封面图下方**的查看成员（members），打开列表成员弹框

   <img width="591" alt="image" src="https://github.com/daymade/Twitter-Block-Porn/assets/4291901/a7f015a1-a34f-4dc6-9ad5-46d7c8655239">

5. 在弹框的右上角有"全部屏蔽"按钮

   <img width="603" alt="image" src="https://github.com/daymade/Twitter-Block-Porn/assets/4291901/a1b5f482-f579-4764-9978-8feb0f1df970">


## 贡献方式

有两种方式:
1. 去 github 上提 issue([示例](https://github.com/daymade/Twitter-Block-Porn/issues/4)), 附上 screen_name 或者 id_str 或者任何可以定位的链接, 我来添加, 你也可以直接 fork 代码后提 PR 给我.
2. 给我一个 List 链接, 我可以直接让用户跳转到你维护的列表.

## 源码地址:

[https://github.com/daymade/Twitter-Block-Porn](https://github.com/daymade/Twitter-Block-Porn)

方便的话给个免费的 STAR 吧 (*╹▽╹*) !

## 实现原理

1. 怎么批量 Block 账号?

   抓包可以看出来在用户点击拉黑某个账号时, 会向 twitter 服务器发送 `/1.1/blocks/create.json` 请求, 用 js 携带用户自己的 cookie 模拟这个请求, 就可以达到自动拉黑的效果.

2. `/1.1/blocks/create.json` 需要 id 参数, 怎么查询账号的 id?

   ```
   # 填入你在 https://developer.twitter.com 申请的 API KEY, 替换 XXX
   export TWITTER_API_KEY="XXX"

   # 调用推特开发者 API, 修改 screen_name 为你要查询的用户名, 可传入多个用逗号分隔
   curl -s -X GET "https://api.twitter.com/1.1/users/lookup.json?screen_name=va77735,annegaga09" \
      -H "Authorization: Bearer $TWITTER_API_KEY" \
      | jq '[.[] | .id_str]'
   ```

3. 怎么自动识别诈骗黄推? 

   使用 https://github.com/daymade/Block-Pornographic-Replies 插件, 用关键字识别

4. 怎么批量管理 twitter 的 List, 自动将诈骗账号添加到 List?

    魔改了 https://github.com/daymade/Block-Pornographic-Replies 插件, 代码见 https://github.com/slarkvan/Block-Pornographic-Replies/compare/main...daymade:Block-Pornographic-Replies:main

## 👨‍💻贡献者/Contributors

我们欢迎任何形式的贡献，无论是提交错误报告，提出改进意见，或者是提供代码和文档。我们都欣赏你的帮助。

贡献者列表：

<a href="https://github.com/daymade/Twitter-Block-Porn/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=daymade/Twitter-Block-Porn" />
</a>


另外，感谢 @albaz64 提供了还原被替换 logo 的思路， 感谢 @aoxu 提供了很多黑名单

---
李老师最可爱
<pre>
                                                                                                   
                                                                                                   
                                                                        ....*...                   
                                                                        .*,@@\..                   
            ..*......  .                ..  .   ......................*.,@@^@@..                   
            .,@@@].... .                   ..   .......*..*........ **,@@`..=@^.                   
            .=@^.[@@\`......    ........*...,]]@@@@@@@@@@@@@@@@@@]].,@@/... =@@.                   
            ..@^....,\@\....    ...**]/@@@@@/[[......*...........[\@@`....  .@@`..                 
            ..\@    ..,@@\...*.,]@@@@[`......@@.....,@@`....                .=@\....               
            ..@@    .....\@]@@@/[..........,@@@@`.*.@/\@`...                .*@@....               
            ../@        ...[*...        ...=@@*,@\.=@^*@@...                ..=@^...               
            ..@/        .....           ...@@@...\@@@...\@**                ...@@`..               
            ..\@                        ..=@@@....,[`....@@*..      ....*.**...=@\..               
            ../@                        ..=@@^............`..       ...,@@`.....@@`*               
            ..=@. ..                    ..=@.`..                    .,@@/...  ..=@\.               
            ..=@....                    ........                  ../@@`....   ..@@*               
            ..=@....    .   ............                       ..................=@^....    ....   
            ..=@^..      ...*]]]]]]*.*..                       ...................@@....    ..*.   
            ..*@^...      ...\@@@@@@@`..        .   . .   ..    .....,O@O`**......=@^....,]@@@@.   
            ...@^...    .   ...... .....         ........       . ..*@@@@@`......./@@@@/[`*.....   
  ..**.........@@...   .....*]]`..            .../@@@@@^. .         .....**.**]@@/`\@`..           
 ...\@@@`......@@...   ...*=@@@/..             ..\@@@@@`.               ...,@[.....=@^*.           
    ....[@@@@]]/@...........[/`*        ......*...,@@/..*....*..........    ...,...,@@..........   
     .........*=@/[\@@@@@/@]*..*.       ..*..]]@@@@@@@@@@@@@@@@@@\`...*.    ...*,[@@@@@@@@@@@@@.   
................@^.......... ........*]]@@@@\@^.... ........,@@@^,[@@@@\.*..      ..*@\.........   
 ......*......]]@@@@@@@@/*..    ..*,@/[..,@\@@..    .......,]/@@@@@@@@@@@...       ..@@*           
...@@@@@@@@@[[[`\@..            .*=@`..*...,[`...,]]@@@@@@@@[[[`..           . ......,@\.......    
............ ...=@..            .*.[@@@@@@@@@@@@@@/*.............            ...\@@\]]@@.......    
                *@^.........        ......  ......                            .......,\@@@@@@\].   
                .=@...../@*.         ..                                          .. ..=@^.......   
           ......=@`.]@/`*..                                                        ..=@^...       
          . ..*,]/@@/`......                                                        ..=@^...       
    ......,/@@@/`*=@....                                                        ......=@^. .       
    ..,/@@/`..*...,@^*..                                                        ...**]/@`..        
     .....      ..*\@...                                                        ...@@@@@^...       
                ...,@^..                                                        ..*,[@@@`...       
                   .\\.....*.*..                                ........,]]]*.........=@^.......   
                   .=@@@@@@@@`..                                ...**/@@/`...*...,/@@@@@\.....*.   
                    .@/[[`*... .            ..,`........        .*/@@`....      .,[[\@@@@@@@/@@*   
                    .@@*.......             ..,\@@@\*...        .,@^....   .    ................   
                    .@@@@@@@\...   .    . . ......*[@\`. . ... ..@@.    ....  ..            ..     
                    .@@@/[[[[...        .............\@`....  ..=@^*.........               .  .   
                    .=@.....    ..]`......]@@@\*.]/@@@@@^*.....=@^,]`.*,@@]`..**    ..........=`   
                    .=@^....    ..[@@]]@@/[*.*@@^@@@@/\@`......@@@@@^@@@@.[@@@@.    ...*]@@@`@@.   
                    ..@@@\`.....    ....     ..=@@@`...     ...\@`.@@@@@/...    .....*./@\.,\@@.   
                    ..@@@@@@@`*.            ....*,`*..      ........[`......    ...*@@@@@@......   
                    .*@@@@@@[\`.                                                ...,@@@@@@`.       
                    ..\@***.....                                                .. ...../@^.       
                                                                                                   
                                                                                                   </pre>
