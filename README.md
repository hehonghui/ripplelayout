# ripplelayout
   这是一个类似于支付宝声波支付的波纹效果布局, 使用了NineOldAnimations动画库,使之可以兼容API 11以下的系统。效果如下:      

<img src="http://img.blog.csdn.net/20150109114245750" alt="" width="200" height="320" style="border:1px solid black">

## 使用示例    
   在布局文件中添加RippleLayout,并且将你的中心视图添加到RippleLayout中，例如 :     
```xml

    <org.simple.ripple.RippleLayout
        xmlns:ripple="http://schemas.android.com/apk/org.simple.ripplelayout"
        android:id="@+id/ripple_layout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        ripple:duration="3000"
        ripple:radius="32dp"
        ripple:rippleNums="1"
        ripple:scale="4"
        ripple:color="#8899CC" >

        <ImageView
            android:id="@+id/centerImage"
            android:layout_width="64dp"
            android:layout_height="64dp"
            android:layout_centerInParent="true"
            android:contentDescription="@string/app_name"
            android:src="@drawable/phone2" />
    </org.simple.ripple.RippleLayout>
```          

    
这样,图片就在RippleLayout的中心,RippleLayout会为你添加通过rippleNums指定的波形数量.   
**注意**,上述布局中引用了xmlns:ripple="http://schemas.android.com/apk/org.simple.ripplelayout"，这是RippleLayout的资源路径，修改成你包路径即可路径。       
   更多详情请参考 : <a href="http://blog.csdn.net/bboyfeiyu/article/details/42552249" target="_blank">Mr.Simple的博客</a> .          
   
   
   
**代码中启动动画**         
   
```java

    ImageView imageview;
    RippleLayout layout;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        layout = (RippleLayout) findViewById(R.id.ripple_layout);
        imageview = (ImageView) findViewById(R.id.centerImage);
        imageview.setOnClickListener(new OnClickListener() {

            @Override
            public void onClick(View v) {
                if (layout.isRippleAnimationRunning()) {
                    layout.stopRippleAnimation();
                } else {
                    layout.startRippleAnimation();
                }
            }
        });
    }
```       


	