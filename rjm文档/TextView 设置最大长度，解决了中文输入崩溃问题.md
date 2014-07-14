//TextView 设置最大长度，解决了中文输入崩溃问题

NSString *toBeString = expandingTextView.text;
    NSString *lang = [[UITextInputMode currentInputMode] primaryLanguage]; // 键盘输入模式
    if ([lang isEqualToString:@"zh-Hans"]) { // 简体中文输入，包括简体拼音，健体五笔，简体手写
        UITextRange *selectedRange = [expandingTextView.internalTextView markedTextRange];
        //获取高亮部分
        UITextPosition *position = [expandingTextView.internalTextView positionFromPosition:selectedRange.start offset:0];
        // 没有高亮选择的字，则对已输入的文字进行字数统计和限制
        if (!position) {
            if (toBeString.length > TEXTVIEW_MAX_LENGHT) {
                expandingTextView.text = [toBeString substringToIndex:TEXTVIEW_MAX_LENGHT];
            }
        }
        // 有高亮选择的字符串，则暂不对文字进行统计和限制
        else{
            
        }
    }
    // 中文输入法以外的直接对其统计限制即可，不考虑其他语种情况
    else{
        if (toBeString.length > TEXTVIEW_MAX_LENGHT) {
            expandingTextView.text = [toBeString substringToIndex:TEXTVIEW_MAX_LENGHT];
        }
    }