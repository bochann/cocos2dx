音量調整

    CocosDenshion::SimpleAudioEngine::getInstance()->setEffectsVolume(flot Volume);


----
音再生

    #include “SimpleAudioEngine”

    CocosDenshion::SimpleAudioEngine::getInstance()->preloadEffect(“音源パス”);

    CocosDenshion::SimpleAudioEngine::getInstance()->playEffect(“音源パス”,”大に引数には何も入れなければ繰り返さない、繰り返したい場合はtrue”);
