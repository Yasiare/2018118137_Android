# Intent的使用

## 一、实验目的：掌握Intent的用法

## 二、实验过程：

###     1、显示Intent：

``` java
 @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.first_layout);
        Button button1 = (Button) findViewById(R.id.button_1);
        button1.setOnClickListener(new View.OnClickListener(){
            @Override
            public void onClick(View v){
                Intent intent = new Intent(FirstActivity.this, SecondActivity.class);
                startActivity(intent);
            }
        });
    }
```

<img src="C:\Git\Lab4\image\1.png" alt="result1" style="zoom:50%;" />