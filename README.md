# Read-Users-From-Server-Library

Step 1 : Create New Android Studio Project
Step 2 : Add it in your root build.gradle at the end of repositories:
```
allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}

```

Step 3 : Add the dependency
```
dependencies {
	        implementation 'com.github.mustafa7745:Android-Studio-Library:1.0.4'
	}
```
Step 3 : Create New Layout Resource File inside Folder  ```res/layout``` With Name ```custom_layout_user``` and Paste This Code inside it  :

```
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="wrap_content">

    <TextView
        android:id="@+id/textView_id"
        android:layout_width="30dp"
        android:layout_height="21dp"
        android:layout_marginStart="16dp"
        android:text="TextView"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView_name"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="200dp"
        android:text="TextView"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="70dp"
        android:layout_height="61dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/textView_name"
        app:layout_constraintHorizontal_bias="0.322"
        app:layout_constraintStart_toEndOf="@+id/textView_id"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.0"
        tools:srcCompat="@tools:sample/avatars" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
Step 4 : Add this Code inside ```activity_main.xml```:

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <androidx.recyclerview.widget.RecyclerView
        android:id="@+id/recycler"
        android:layout_width="391dp"
        android:layout_height="624dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.728" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
Step 5 : Paste this Code inside ```MainActivity.class``` :
```
 //   Use This Variable With Same Name
    int custom_layout_user=R.layout.custom_layout_user;
    int textView_id=R.id.textView_id;
    int textView_name=R.id.textView_name;
    int imageView=R.id.imageView;

    //   Place Your URl Inside Variable url as String
    String url="https://elctronics-tech.000webhostapp.com/read.php";

    //Define These Variable
    RecyclerView recyclerView;
    RecyclerView.Adapter adapter;
    RecyclerView.LayoutManager layoutManager;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        //   Place this Code Here
        recyclerView=findViewById(R.id.recycler);
        Toaster toaster=new Toaster(this,layoutManager,adapter,recyclerView,custom_layout_user ,textView_id , textView_name,imageView,url);
        toaster.readDataFromDatabase();

    }
```

Step 6 : Run The Project and Fun 👍 
