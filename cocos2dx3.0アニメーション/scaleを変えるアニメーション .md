scaleを変えるアニメーション
ScaleTo

    auto action = ScaleTo::create(3,2,”ここにfloatの値を入れる事により横のサイズのスケールを変更できる”);

    mySptite->runAction(action);


------
scaleを変えるアニメーション(逆)
ScaleBy

    auto action = ScaleBy::create(3,3,”ここにfloatの値を入れる事により横のサイズのスケールを変更できる”);

    mySptite->runAction(action);

