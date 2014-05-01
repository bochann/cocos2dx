###BGMの再生がsharedEngineからgetInstanceになった。
旧:(.cpp)


    //BGMプリロード

    CocosDenshion::SimpleAudioEngine::sharedEngine()->preloadBackgroundMusic("bgm_main01.mp3");


    //BGM再生

    CocosDenshion::SimpleAudioEngine::sharedEngine()->playBackgroundMusic("bgm_main01.mp3", true);


    //BGM停止

    CocosDenshion::SimpleAudioEngine::sharedEngine()->stopBackgroundMusic();


新:(.cpp)


    //音量初期設定

    CocosDenshion::SimpleAudioEngine::getInstance()->setBackgroundMusicVolume(0.5f);


    //BGMプリロード

    CocosDenshion::SimpleAudioEngine::getInstance()->preloadBackgroundMusic("bgm_main01.mp3");


    //BGM再生

    CocosDenshion::SimpleAudioEngine::getInstance()->playBackgroundMusic("bgm_main01.mp3", true);


    //BGM停止

    CocosDenshion::SimpleAudioEngine::getInstance()->stopBackgroundMusic();

