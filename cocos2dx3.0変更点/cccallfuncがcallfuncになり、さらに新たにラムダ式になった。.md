###CCCallFuncがCallFuncになり、さらに新たにラムダ式になった。


旧:

    CCCallFunc *func01 =CCCallFunc::create(this, callfunc_selector(Player::action));

    this->runAction(func01);

新:


    cocos2d::CallFunc *func01 = CallFunc::create([this]()

    {

    this->action();

    });//:CallFunc

    this->runAction(func01);
