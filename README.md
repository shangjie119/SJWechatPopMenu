# SJWechatPopMenu
仿微信聊天功能菜单

SJPopMenu使用方法：
1. 显示： [[SJPopMenu menu] showBy:xxxxxx]
2. 需实现 SJCustomSelectTextView 里面方法，如果是自定义textView，只需将 SJCustomSelectTextView 的父类改为项目使用的textView即可
3. controller中需实现3个方法并且发送通知，使滚动时正确显示menu
```
- (void)scrollViewDidScroll:(UIScrollView *)scrollView{
    [[NSNotificationCenter defaultCenter] postNotificationName:@"SJChangePopMenuIfNeeded" object:nil];
}

- (void)scrollViewDidEndDecelerating:(UIScrollView *)scrollView
{
    [[NSNotificationCenter defaultCenter] postNotificationName:@"SJShowPopMenuIfNeeded" object:nil];
}

- (void)scrollViewDidEndDragging:(UIScrollView *)scrollView willDecelerate:(BOOL)decelerate {
    if (!decelerate) {
        [[NSNotificationCenter defaultCenter] postNotificationName:@"SJShowPopMenuIfNeeded" object:nil];
    }
}
```
4. 点击menu action回调使用 menu.itemActions 



https://user-images.githubusercontent.com/7741844/177238042-b0cf9e1e-1aa2-4f44-8c1a-8fa8a303f25e.mp4

