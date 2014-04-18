#####CCDictionaryで保存する

#####ファイルの書き込み


結構びっくりするくらい簡単です。
手順としては、

CCDirectoryを作成
中にいろいろ入れる(CCString、CCArray、CCDictionaryのみ）
writeToFileメソッドを呼び出す
ちなみにplist形式で書き出されるらしいのですが、拡張子は何でもOK。


    CCDirectory* savedir = CCDirectory::create();
    //保存する配列を作成
    //ccs = CCString::createと同じです。CCString.h内で定義されています。
    CCArray* ary = CCArray::create(ccs("arytest1"),ccs("arytest2"),NULL);
    savedir->setObject(ary , "testArray");
    //保存する辞書を作成
    CCDictionary* dic = CCDictionary::create();
    dic->setObject(ccs("1"),"dic1");
    dic->setObject(ccs("2"),"dic2");
    savedir->setObject(dic , "testDic");
    //保存するCCStringを作成
    CCString* str = CCString::create("true");
    savedir->setObject(str , "testBool");
 
    //保存箇所のフルパスを取得
    std::string savepath = CCFileUtils::sharedFileUtils()->getWritablePath() + "savadata.svd";
    //保存
    if(savedir->writeToFile(savepath)){
       CCLOG("save Success:%s" , savepath);
    }else{
       CCLOG("save Failed:%s" , savepath);
    }
    
 ------------------------------------------------------
 
#####ファイルの読み込み

これもとっても簡単です。フルパスでcreateWithContentsOfFileを呼び出せば、あとは普段のCCDictionaryと同じように扱えます。

    std::string savepath = CCFileUtils::sharedFileUtils()->getWritablePath() + "savadata.svd";
    //存在するかどうか確認
    CCDictionary* dic = NULL;
    if(CCFileUtils::sharedFileUtils()->isFileExist(savepath)){
       dic = CCDictionary::createWithContentsOfFile(savepath.c_str());
    }else{
       dic = CCDictionary::create();
    }

---------------------------------------------------------

＊補足

保存場所のパスは以下のような感じで簡単に取得することができます。

    CCFileUtils::sharedFileUtils()->getWritablePath();