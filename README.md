# 19273027_권미사

## 1주차 과제

Hello My name is Kwon misa


## 2주차 과제
  ![2주차](https://user-images.githubusercontent.com/71074287/93702738-41ea8500-fb52-11ea-8059-e6b09adeb245.PNG)

## 3주차 과제
  ![3주차 1](https://user-images.githubusercontent.com/71074287/93703047-5a5a9f80-fb52-11ea-9c37-4d589e27954d.PNG)
  ![3주차 2](https://user-images.githubusercontent.com/71074287/93703084-5cbcf980-fb52-11ea-99de-dc98152cf2e1.PNG)
  ![3주차 3](https://user-images.githubusercontent.com/71074287/93703104-5dee2680-fb52-11ea-88a9-4156d2a8ba7d.PNG)


## 4주차 과제
### 원하는 물건이 매장에 있는지 없는지 알려주는 앱
-기능 : 앱과 제휴한 회사의 점포의 물건의 가격과 재고, 재고품의 입고 예정일과 시간 제공

-앱이 만들어진 이유 : 소비자의 헛걸음을 방지하기 위함

+요소 : 물건의 예약구매(찜하기) 기능


이용시설 : 편의점, 마트, 슈퍼, 개인매장, 백화점, 등등 레저시설에서의 레저용품 개수 또한 가능

소비자가 구매하고자 하는 물건이라면 무엇이든 재고부족으로 인한 소비자의 헛걸음을 방지하기 위한 재고수량 정보 제공,

택배비 지불시 택배로 상품배달 가능

![inventory](https://user-images.githubusercontent.com/71074287/94363598-425cc000-00fe-11eb-8f4d-9d9eef6ff0cb.png)


## 7주차 과제

  ![7주차1](https://user-images.githubusercontent.com/71074287/96360592-7ead9a00-1159-11eb-9299-0177336e3980.PNG)
  ![7주차2](https://user-images.githubusercontent.com/71074287/96360593-82412100-1159-11eb-81fd-65341a63cc4a.PNG)


## 9주차 과제
### 첫번째 사진
![9-1](https://user-images.githubusercontent.com/71074287/97804744-23b98e00-1c95-11eb-9fdd-6f9397478b0d.PNG)
### 이미지 바꾸기 버튼을 누른 사진
![9-2](https://user-images.githubusercontent.com/71074287/97804745-25835180-1c95-11eb-8a50-30ca177eacab.PNG)
### 넓이 버튼 사진
![9-3](https://user-images.githubusercontent.com/71074287/97804747-261be800-1c95-11eb-9e29-97ed9736ec6c.PNG)
### 높이 버튼 사진
![9-4](https://user-images.githubusercontent.com/71074287/97804748-274d1500-1c95-11eb-81c0-87e906968192.PNG)
### xml코드
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <Button
        android:id="@+id/btn1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:layout_marginTop="5dp"
        android:text="이미지 바꾸기"
        android:onClick="btn1Clicked"
        />
    <Button
        android:id="@+id/btn2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:layout_marginTop="5dp"
        android:text="넓이"
        android:onClick="btn2Clicked"
        />
    <Button
        android:id="@+id/btn3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:layout_marginTop="5dp"
        android:text="높이"
        android:onClick="btn3Clicked"
        />
    <HorizontalScrollView
        android:id="@+id/horScrollView"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
        <ScrollView
            android:id="@+id/verScrollView"
            android:layout_width="match_parent"
            android:layout_height="match_parent">
            <ImageView
                android:id="@+id/imageView"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                />
        </ScrollView>
    </HorizontalScrollView>
</LinearLayout>

### java코드
package com.example.week9;

import androidx.appcompat.app.AppCompatActivity;

import android.content.res.Resources;
import android.graphics.drawable.BitmapDrawable;
import android.os.Bundle;
import android.view.View;
import android.widget.ImageView;
import android.widget.ScrollView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    ScrollView scrollView;
    ImageView imageView;
    BitmapDrawable bitmap;
    String imageWidth;
    String imageHeight;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        scrollView = findViewById(R.id.verScrollView);
        imageView = findViewById(R.id.imageView);
        scrollView.setHorizontalScrollBarEnabled(true);

        Resources res = getResources();
        bitmap = (BitmapDrawable) res.getDrawable(R.drawable.image01);
        int bitmapWidth = bitmap.getIntrinsicWidth();
        int bitmapHeight = bitmap.getIntrinsicHeight();
        imageWidth =Integer.toString(bitmapWidth);
        imageHeight =Integer.toString(bitmapHeight);

        imageView.setImageDrawable(bitmap);
        imageView.getLayoutParams().width = bitmapWidth;
        imageView.getLayoutParams().height = bitmapHeight;
    }

    public void btn1Clicked(View v)
    {
        changeImage();
    }

    private void changeImage()
    {
        Resources res = getResources();
        bitmap = (BitmapDrawable) res.getDrawable(R.drawable.image02);
        int bitmapWidth = bitmap.getIntrinsicWidth();
        int bitmapHeight = bitmap.getIntrinsicHeight();

        imageView.setImageDrawable(bitmap);
        imageView.getLayoutParams().width = bitmapWidth;
        imageView.getLayoutParams().height = bitmapHeight;
    }

    public void btn2Clicked(View v)
    {
        Toast.makeText(this,imageWidth,Toast.LENGTH_SHORT).show();
    }

    public void btn3Clicked(View v)
    {
        Toast.makeText(this,imageHeight,Toast.LENGTH_LONG).show();
    }
}



## 10주차 과제
![화면 캡처 2020-11-08 193339](https://user-images.githubusercontent.com/71074287/98462728-b01a0280-21f9-11eb-90de-94c242ede794.png)
![화면 캡처 2020-11-08 193357](https://user-images.githubusercontent.com/71074287/98462732-b60fe380-21f9-11eb-928b-549c53655d5d.png)
![화면 캡처 2020-11-08 193515](https://user-images.githubusercontent.com/71074287/98462739-bb6d2e00-21f9-11eb-9328-0c7c9463d108.png)
![화면 캡처 2020-11-08 193600](https://user-images.githubusercontent.com/71074287/98462747-c45dff80-21f9-11eb-9a99-fe46aca63817.png)
### xml코드
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_weight="1"
        android:orientation="vertical">

        <TextView
            android:id="@+id/xinputCount"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="0 / 80 바이트"
            android:layout_gravity="right"
            android:layout_marginTop="10dp"
            android:textColor="#ff0000ff"
            android:textSize="20sp" />
        <EditText
            android:id="@+id/xinputMessage"
            android:layout_width="300dp"
            android:layout_height="500dp"
            android:maxLength="80"
            android:layout_gravity="center_horizontal"
            android:textSize="36sp" />
    </LinearLayout>
    <LinearLayout
        android:orientation="horizontal"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:gravity="center"
        android:layout_weight="3">

        <Button
            android:id="@+id/xsendButton"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="top"
            android:layout_margin="20dp"
            android:paddingLeft="20dp"
            android:paddingRight="20dp"
            android:text="전송"
            android:textSize="18sp"
            />
        <Button
            android:id="@+id/xcloseButton"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="top"
            android:layout_margin="20dp"
            android:paddingLeft="20dp"
            android:paddingRight="20dp"
            android:text="닫기"
            android:textSize="18sp"
            />
    </LinearLayout>
</LinearLayout>

### java코드
package com.example.a10week;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.text.Editable;
import android.text.TextWatcher;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import java.io.UnsupportedEncodingException;

public class MainActivity extends AppCompatActivity {
    EditText jinputMessage;
    TextView jinputCount;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        jinputMessage = findViewById(R.id.xinputMessage);
        jinputCount = findViewById(R.id.xinputCount);

        Button jsendButton = findViewById(R.id.xsendButton);
        jsendButton.setOnClickListener(new View.OnClickListener(){
            public void onClick(View v){
                String message = jinputMessage.getText().toString();
                Toast.makeText(getApplicationContext(),"전송할 메시지\n\n" + message,Toast.LENGTH_LONG).show();
            }
        });

        Button jcloseButton = findViewById(R.id.xcloseButton);
        jcloseButton.setOnClickListener(new View. OnClickListener(){
            public void onClick(View v){
                finish();
            }
        });

        TextWatcher watcher = new TextWatcher() {
            public void onTextChanged(CharSequence str, int start, int before, int count) {
                byte[] bytes = null;
                try {
                    bytes = str.toString().getBytes( "KSC5601");
                    int strCount = bytes.length;
                    jinputCount.setText(strCount + " / 80바이트");
                } catch(UnsupportedEncodingException ex) {
                    ex.printStackTrace();
                }
            }

            public void beforeTextChanged(CharSequence s, int start, int count, int after) {

            }

            public void afterTextChanged(Editable strEditable) {
                String str = strEditable.toString();
                try {
                    byte[] strBytes = str.getBytes( "KSC5601");
                    if(strBytes.length > 80) {
                        strEditable.delete(strEditable.length()-2, strEditable.length()-1);
                    }
                } catch(Exception ex) {
                    ex.printStackTrace();
                }
            }

        };
        jinputMessage.addTextChangedListener(watcher);
    }
}
