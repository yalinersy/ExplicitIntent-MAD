# Ex.No:3b To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as ImplicitIntent and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.


## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: Sri Yaline R
Registeration Number : 212224040325
*/

MainActivity.Java

package com.example.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        EditText etNum1 = findViewById(R.id.etNum1);
        EditText etNum2 = findViewById(R.id.etNum2);
        Button btnGo = findViewById(R.id.btnGo);

        btnGo.setOnClickListener(v -> {
            String val1 = etNum1.getText().toString();
            String val2 = etNum2.getText().toString();

            if (!val1.isEmpty() && !val2.isEmpty()) {
                int n1 = Integer.parseInt(val1);
                int n2 = Integer.parseInt(val2);
                int sum = n1 + n2;

                Intent intent = new Intent(MainActivity.this, SecondActivity.class);
                intent.putExtra("SUM_RESULT", sum);
                startActivity(intent);
            }
        });
    }
}


SecondActivity.Java

package com.example.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_second);

        TextView tvResult = findViewById(R.id.tvResult);
        
        // Receive the data from Intent
        int result = getIntent().getIntExtra("SUM_RESULT", 0);
        tvResult.setText(getString(R.string.sum_result, result));

        // Button click → Go back to MainActivity
        Button btnGoBack = findViewById(R.id.btnGoBack);
        btnGoBack.setOnClickListener(v -> {
            finish();
        });
    }
}


activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <!-- Title -->
    <TextView
        android:id="@+id/textView1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/explicit_intent"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="50dp"/>

    <TextView
        android:id="@+id/tvSubtitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/first_activity"
        android:textSize="18sp"
        app:layout_constraintTop_toBottomOf="@id/textView1"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="8dp"/>

    <EditText
        android:id="@+id/etNum1"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:hint="@string/enter_first_number"
        android:importantForAutofill="no"
        android:inputType="number"
        android:minHeight="48dp"
        android:layout_marginTop="32dp"
        app:layout_constraintTop_toBottomOf="@id/tvSubtitle"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"/>

    <EditText
        android:id="@+id/etNum2"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:hint="@string/enter_second_number"
        android:importantForAutofill="no"
        android:inputType="number"
        android:minHeight="48dp"
        android:layout_marginTop="16dp"
        app:layout_constraintTop_toBottomOf="@id/etNum1"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"/>

    <!-- Button -->
    <Button
        android:id="@+id/btnGo"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/add_and_go"
        android:minHeight="48dp"
        app:layout_constraintTop_toBottomOf="@id/etNum2"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="32dp"/>
</androidx.constraintlayout.widget.ConstraintLayout>


activity_second.xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".SecondActivity">

    <!-- Title -->
    <TextView
        android:id="@+id/textViewTitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/explicit_intent"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="50dp"/>

    <TextView
        android:id="@+id/tvSubtitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/second_activity"
        android:textSize="18sp"
        app:layout_constraintTop_toBottomOf="@id/textViewTitle"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="8dp"/>

    <TextView
        android:id="@+id/tvResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/result_placeholder"
        android:textSize="20sp"
        app:layout_constraintTop_toBottomOf="@id/tvSubtitle"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="50dp"/>

    <!-- Button -->
    <Button
        android:id="@+id/btnGoBack"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/go_to_home"
        app:layout_constraintTop_toBottomOf="@id/tvResult"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="50dp"/>
</androidx.constraintlayout.widget.ConstraintLayout>
```

## OUTPUT
<img width="1920" height="1200" alt="Screenshot 2026-04-28 204831" src="https://github.com/user-attachments/assets/b1c0f05b-dfde-4183-b053-6437463134d8" />
<img width="1920" height="1200" alt="Screenshot 2026-04-28 204839" src="https://github.com/user-attachments/assets/5e3ca9a0-cdd6-4374-b9ce-df513d094e49" />




## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


