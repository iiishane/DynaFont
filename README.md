## UILabel+dynaFont用法

预设多种字体大小，支持动态切换

具体用法：

设置字体：
```
 UILabel *testLabel = [[UILabel alloc]init];
 设置方式一(用于设置默认字体样式[UIFont systemFontOfSize:])：
 [testLabel setDyna_fontSize:DynaFontSizeMake(10, 10, 12)];

设置方式二(用于设置自定义字体样式)：
[testLabel setDyna_fontSizeBlock:^(WIFontSizeModel model) {
            int fontSize = 10;
            switch (model) {
                case WIFontSizeModelSmall: fontSize = 10;
                    break;
                case WIFontSizeModelBig: fontSize = 12;
                    break;
                default:
                    break;
            }
            [testLabel setFont:[UIFont italicSystemFontOfSize:fontSize]];//设置自定义字体
        }];

```

应用内全局修改字体大小：
```
发送大字体模式广播示例：
[[NSNotificationCenter defaultCenter] postNotification:[NSNotification notificationWithName:WIDynamicChangeFontSizeNotification object:@(WIFontSizeModelBig) userInfo:nil]];

```
