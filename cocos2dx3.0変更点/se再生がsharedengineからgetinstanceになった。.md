###SE再生がsharedEngineからgetInstanceになった。

旧:(.cpp)


    //SEプリロード

    CocosDenshion::SimpleAudioEngine::sharedEngine()->preloadEffect("se_button_push.mp3");


    //SE再生

    CocosDenshion::SimpleAudioEngine::sharedEngine()->playEffect("se_button_push.mp3");


新:(.cpp)


    //音量初期設定

    CocosDenshion::SimpleAudioEngine::getInstance()->setEffectsVolume(0.5f);


    //SEプリロード

    CocosDenshion::SimpleAudioEngine::getInstance()->preloadEffect("se_button_push.mp3");


    //SE再生

    CocosDenshion::SimpleAudioEngine::getInstance()->playEffect("se_button_push.mp3", //ファイルネーム
                                                            false, //ループするか否か
                                                            1.0f, //再生ピッチ
                                                            0.0f, //パン(-1.0f～1.0f。0.0fが中心)
                                                            1.0f //音量
                                                            );



