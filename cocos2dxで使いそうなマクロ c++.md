  **cocos2dxで使いそうなマクロ c++**

----------------------------------------------------
  
    CC_SAFE_DELETE(ポインタ) 使いそう度：★★★ (13/08/06)


名前のとおりセーフティーにdeleteしてくれる。

-----------------------------------------------------

    CC_SAFE_DELETE_ARRAY(配列ポインタ) 使いそう度：★★(13/08/06)

CC_SAFE_DELETEの配列バージョン。

------------------------------------------------------
 
    CC_SAFE_RELEASE(CCObject*) 使いそう度：★★★★(14/01/20)

CCObjectがNULLでない場合はrelease()をしてくれます。


--------------------------------------------------------
**※release()に関して**



    CC_SAFE_RELEASE_NULL(CCObject*) 使いそう度：★★★★★(14/01/20)

CC_SAFE_RELEASEをした後、そのメンバをNULLにしてくれる。
メンバ変数はデストラクタ時にはNULLにする方がいいらしいので、そうしとくと安心ですね。

-------------------------------------------------------

    CC_SYNTHESIZE(メンバ,名前,関数名)使いそう度：★★★★★(14/01/20)

protectedメンバとそれを取り出すpublic関数、セットするpublic関数を自動生成してくれる。


//CC_SYNTHESIZE(hoge , m_hoge , Hoge);
//↓以下のようになる
protected: hoge m_hoge;
public:virtual hoge getHoge(void) const { return m_hoge; }
public:virtual void setHoge(hoge var){ m_hoge = var; }
使用上の注意としては、public:宣言される為private:やprotected:で宣言しなおさないと下のは全部publicになる。もうpublicにする予定の場所に書いておけばいいみたい。

似たようなのではメンバの参照をセット＆返すCC_SYNTHESIZE_PASS_BY_REFがある。
あとCCObjectを安全にセットできるCC_SYNTHESIZE_RETAINがある。
これはsetFunc()した場合、
１)中で前まで所持してたものをrelease()し、続いて
２)新しくセットするものをretain()してくれる仕組みになってます。

------------------------------------------------------

    CC_SYNTHESIZE_READONLY(メンバ,名前,関数名)使いそう度：★★★★★(13/08/06)

protected メンバとそれを取り出すpublic関数を自動生成してくれる。



//CC_SYNTHESIZE_READONLY(hoge , m_hoge , Hoge);
//↓以下のようになる
protected: hoge m_hoge;
public: virtual hoge getHoge(void) const { return m_hoge; }
これも使用上の注意としては、public:宣言される為private:やprotected:で宣言しなおさないと下のは全部publicになる。もうpublicにする予定の場所に書いておけばいいみたい。

似たようなのではメンバの参照を返すCC_SYNTHESIZE_READONLY_PASS_BY_REFがある。

CC_UNUSED_PARAM(引数) 使いそう度：★★(13/08/06)

cocos2dxの継承クラスでオーバーライドした関数の引数を中で使わないのであれば呼び出しとけばいいみたい(コンパイル時にwarningがでなくなる？)

--------------------------------------------------------

    CCLOG(書式,…) 使いそう度：★★★★★(14/01/20)

ログを吐き出してくれるデバッグには欠かせないマクロです。中身はCCLogを実行してるだけなんだけど、デバッグモードをOFFにするとログを吐き出さなくなるのでとても安全に使えます。


-------------------------------------------------------

    CREATE_FUNC(クラス名) 使いそう度：★★★★★ (13/08/06)

(cocos2dで使うクラス).create();を定義＆実装してくれるっぽい。
更にインスタンスが必要なくなったら自動でメモリ解放もしてくれるようになるみたい。
これをヘッダファイルに書いておけばcreate()の実装をかかなくてもよくなる。

--------------------------------------------------------
