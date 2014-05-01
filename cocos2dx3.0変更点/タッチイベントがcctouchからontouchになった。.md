###タッチイベントがccTouchからonTouchになった。

旧:(.h)


    //[タッチイベント]

    virtual void ccTouchesBegan(CCSet *pTouches, CCEvent *pEvent);

    virtual void ccTouchesMoved(CCSet *pTouches, CCEvent *pEvent);

    virtual void ccTouchesEnded(CCSet *pTouches, CCEvent *pEvent);

    virtual void ccTouchesCancelled(CCSet *pTouches, CCEvent *pEvent);  



新:(.h)


    //[タッチイベント]

    virtual void onTouchesBegan(const std::vector& touches, Event *unused_event);

    virtual void onTouchesMoved(const std::vector& touches, Event *unused_event);

    virtual void onTouchesEnded(const std::vector& touches, Event *unused_event);

    virtual void onTouchesCancelled(const std::vector& touches, Event *unused_event);
    
※以下はcocos2d::Layerを継承したクラス[TouchLayer]に実装しています。

新:(.cpp)


    //[タッチイベント]

    void TouchLayer::onTouchesBegan(const std::vector& touches, Event *unused_event)

    {

	//タッチの分だけ繰り返す

	for (auto touchObject : touches)

	{

		//タッチの内容がある場合のみ実行

		if(touchObject != nullptr)

		{

			//タッチされた場所を取得

			cocos2d::Point touchLocation = touchObject->getLocationInView();

			touchLocation = Director::getInstance()->convertToGL(touchLocation);

			CCLOG("タッチロケーション[x:%f][y:%f]" ,touchLocation.x, touchLocation.y);



			//処理を実行(ついでに引数でタッチ場所を送りました)

			this->touchEvent(touchLocation);

		}//:if_else

	}//:for

    }



    void TouchLayer::onTouchesMoved(const std::vector& touches, Event *unused_event){}

    void TouchLayer::onTouchesEnded(const std::vector& touches, Event *unused_event){}

    void TouchLayer::onTouchesCancelled(const std::vector& touches, Event *unused_event){}

続いて、タッチのON OFF用メソッド3.0版

新:(.h)
 
    virtual void touchON(); //タッチ入力感知ON

    virtual void touchOFF(); //タッチ入力感知OFF



新:(.cpp)


    //タッチ入力感知ON

    void TouchLayer::touchON()

    {

	CCLOG("タッチ感知をONにします。");

	auto dispatcher = Director::getInstance()->getEventDispatcher();

	this->touchListener->onTouchesBegan = CC_CALLBACK_2(TouchLayer::onTouchesBegan, this);

	this->touchListener->onTouchesMoved = CC_CALLBACK_2(TouchLayer::onTouchesMoved, this);

	this->touchListener->onTouchesEnded = CC_CALLBACK_2(TouchLayer::onTouchesEnded, this);

	this->touchListener->onTouchesCancelled = CC_CALLBACK_2(TouchLayer::onTouchesCancelled, this);

	dispatcher->addEventListenerWithSceneGraphPriority(this->touchListener, this);

    }



    //タッチ入力感知OFF

    void TouchLayer::touchOFF()

    {

	CCLOG("タッチ感知をOFFにします。");

	auto dispatcher = Director::getInstance()->getEventDispatcher();

	dispatcher->removeEventListener(this->touchListener);

    }
