###CCArrayがVectorという形式に変更になった。

旧：(CCArrayの定義と、オブジェクトの追加)


	CCArray *mokemokeArray;

	CCSprite *spriteObject= CCSprite::create("mokemoke.png");

	objectArray->addObject(spriteObject);		



新：(Vector Arrayの定義と、オブジェクトの追加)


	Vector objectArray;

	cocos2d::Sprite *spriteObject = cocos2d::Sprite::create("mokemoke.png");

	objectArray.pushBack(spriteObject);
