ボタンを押すと画面が推移する。cocos2dx 3.0


    auto button = MenuItemFont::create("BUTTON", [&](Object* sender) {

    Scene *scene = Scene::create();
                                       Director::getInstance()->replaceScene(scene);
                                   });
    Menu *menu = Menu::createWithItem(button);
    addChild(menu);