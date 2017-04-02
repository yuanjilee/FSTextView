# FSTextView
继承于UITextView的自定义TextView, 带placeholder和可限制最大输入字符数, 已适配横竖屏切换, 最低支持iOS6.<p>
2017/04/02 更新 `version 1.1`: <p>
更换注册通知的方式, 避免影响其它的 `FSTextView` 实例.

##### 支持使用CocoaPods引入, Podfile文件中添加:

```objc
pod 'FSTextView', '~> 1.1'
```

注: 使用CocoaPods引入的话, 纯代码创建没有任何问题, 但在Storyboard中设置时会提示 `Fail to update auto layout status: Fail to load designables from path (null)`解决办法是在Podfile文件中添加`use_frameworks!`在`target 'YourProjectName' do`前即可, 但这个方法只能是iOS8及往后版本才行, 如果你的项目版本支持的是iOS7及之前版本的话会报错, 或者你可以找到`Pod`文件夹中`FSTextView`的源码, 删除`FSTextView.h`中的`IB_DESIGNABLE`字段（删除后就没有了Storyboard中`FSTextView`的相关属性即设置即显示的效果）.<p>
基本使用方法:<p>

```objc
FSTextView *textView = [FSTextView textView];
textView.placeholder = @"这是一个继承于UITextView的带Placeholder的自定义TextView, 可以设定限制字符长度, 以Block形式回调, 简单直观 !";
// 限制输入最大字符数.
textView.maxLength = 10;
// 添加输入改变Block回调.
[textView addTextDidChangeHandler:^(FSTextView *textView) {
    // 文本改变后的相应操作.
}];
// 添加到达最大限制Block回调.
[textView addTextLengthDidMaxHandler:^(FSTextView *textView) {
    // 达到最大限制数后的相应操作.
}];
```

竖屏状态<p>
![Alt text][image-1]

横屏状态<p>
![Alt text][image-2]

##### 目前已知的小问题: (不影响使用, Xcode8.3 已修复了这个问题)
在Storyboard中设置Placeholder颜色不会在Storyboard上马上呈现, 但是其实已经修改成功的了, 运行时Placeholder的颜色会是你所设置的颜色.<p>

# LICENSE
FSTextView is available under the MIT license. See the LICENSE file for more info.

[image-1]:http://oeysrv69b.bkt.clouddn.com/FSTextView1.jpg
[image-2]:http://oeysrv69b.bkt.clouddn.com/FSTextView2.jpg


