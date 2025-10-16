# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.

## AIM:
To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.

## EQUIPMENTS REQUIRED:
Latest Version Android Studio

## ALGORITHM:

Step 1: Create a New Project in Android Studio

Step 2: Working with the activity_main.xml File

Step 3: Working with the MainActivity File

Step 4: Working with the activity_main2.xml File

Step 5: Working with the MainActivity2 File

## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: YASHWANTH RAJA DURAI V
Registeration Number : 212222040184
*/
```
### In activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/linearLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#EFF2F4"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/input_field"
        android:layout_width="252dp"
        android:layout_height="48dp"
        android:hint="Enter a number"
        android:inputType="number"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/factorial_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:backgroundTint="#D26BDA"
        android:text="FIND FACTORIAL"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/input_field" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="261dp"
        android:layout_height="99dp"
        android:text="FACTORIAL FINDER"
        android:textAlignment="center"
        android:textColor="#AE218F"
        android:textSize="34sp"
        android:textStyle="bold|italic"
        app:layout_constraintBottom_toTopOf="@+id/input_field"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.72" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
### In MainActivity.java
```
package com.example.explicitintent;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity1);

        // Get references to UI elements
        final EditText inputField = findViewById(R.id.input_field);
        Button factorialButton = findViewById(R.id.factorial_button);

        // Set up the "Explicit Intent" button
        factorialButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Get the input number from the text field
                int inputNumber = Integer.parseInt(inputField.getText().toString());

                // Create an Intent to start the FactorialActivity
                Intent explicitIntent = new Intent(MainActivity.this, MainActivity2.class);
                // Pass the input number as an extra
                explicitIntent.putExtra("input_number", inputNumber);

                // Start the FactorialActivity
                startActivity(explicitIntent);
            }
        });
    }
}
```
### In activity_main2.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#EFF2F4"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/result_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="The Factorial is : "
        android:textColor="#AE218F"
        android:textSize="34sp"
        android:textStyle="bold|italic"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.349" />

    <Button
        android:id="@+id/button"
        android:layout_width="122dp"
        android:layout_height="65dp"
        android:backgroundTint="#C362CA"
        android:onClick="back"
        android:text="BACK"
        android:textColorLink="#C85A5A"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/result_text_view" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
### In MainActivity2.java
```
package com.example.explicitintent;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
import java.math.BigInteger;

public class MainActivity2 extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Get the input number from the Intent extra
        int inputNumber = getIntent().getIntExtra("input_number", 0);

        // Calculate the factorial of the input number using BigInteger
        BigInteger factorial = BigInteger.ONE;
        for (int i = 2; i <= inputNumber; i++) {
            factorial = factorial.multiply(BigInteger.valueOf(i));
        }
        // Display the factorial result in a TextView
        TextView resultTextView = findViewById(R.id.result_text_view);
        resultTextView.setText("Factorial of " + inputNumber + " is: " + factorial);
    }
    public void back(View view) {
        Intent i = new Intent(getApplicationContext(), MainActivity.class);
        startActivity(i);
    }
}
```

## OUTPUT
![WhatsApp Image 2024-03-18 at 09 27 01_a9778e34](https://github.com/AnnBlessy/ExplicitIntent-MAD/assets/119477835/b3d18fd4-289f-4577-b1ec-98669bd19de5) __  ![WhatsApp Image 2024-03-18 at 09 27 02_7e706958](https://github.com/AnnBlessy/ExplicitIntent-MAD/assets/119477835/f9aac70d-92cf-4f59-bf65-afa56e23c3d0)

## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.
