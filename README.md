# Java-Event-Track

## Original Project

<details>
  <summary> ADD PHOTO Welcome Screen </summary>
</details>

<details>
  <summary>Project Description</summary>

The origin of this school project is to create an Event-Tracking app that stores dates and times of upcoming events by allowing users to enter event details. The app displays events on the home screen in a grid view format. Users can add, remove, and edit event details. Data is stored in two database tables, one for login information and the other for event data. This project demonstrates my ability to create a locally stored SQLite database on Android. This project was completed initially using Java with Android Studio on 12/15/24.

</details>

## Enhanced Project

<details>
  <summary>
    Enhancement Plan
  </summary>
</details>

<details>
  <summary>Enhancements Completed</summary>
</details>

<details open>
  <summary>Enhanced Database Code</summary>
  
 ```Java
  public class SignUpDBHelper extends SQLiteOpenHelper {

    // Variables to create database
    private static final String DATABASE_NAME = "userdb";
    private static final int DATABASE_VERSION = 1;
    private static final String TABLE_NAME = "signup";
    private static final String COLUMN_ID = "id";
    private static final String COLUMN_EMAIL = "email";
    private static final String COLUMN_PASSWORD = "password";

    // DB Constructor
    public SignUpDBHelper(Context context){
        super(context, DATABASE_NAME, null, DATABASE_VERSION);
    }

    // Create DB by running SQLite query
    @Override
    public void onCreate(SQLiteDatabase db) {
        String query = "CREATE TABLE " + TABLE_NAME + " ( "
                + COLUMN_ID + " INTEGER PRIMARY KEY AUTOINCREMENT, "
                + COLUMN_EMAIL + " TEXT,"
                + COLUMN_PASSWORD + " TEXT)";
        // Execute query
        db.execSQL(query);
    }

    // Add user info into DB
    public void addNewUser(String userEmail, String userPassword){
        // Call writable method
        SQLiteDatabase db = this.getWritableDatabase();
        // Variable for content values
        ContentValues values = new ContentValues();

        // Pass values in with key and value pair
        values.put(COLUMN_EMAIL, userEmail);
        values.put(COLUMN_PASSWORD, userPassword);

        // Insert values into table
        db.insert(TABLE_NAME, null, values);

        // Close DB
        db.close();
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion){
        // Checks if table already exists
        db.execSQL("DROP TABLE IF EXISTS " + TABLE_NAME);
        onCreate(db);
    }
}
```
</details>



<details>
  <summary>Enhanced Project Review</summary>

This enhancement proved to be a more significant undertaking than I initially anticipated. Initially, the app didn’t run, so I had to perform significant debugging to get it working with the database. While working on the database, I encountered an issue trying to understand my chosen naming conventions. Many items were named poorly, lacking descriptive details, and were labeled simply as “buttons 1, 2, etc.” Trying to decipher it was frustrating, so I decided it was best to scrap the entire project and start again from scratch. After revising the entire project with more descriptive naming conventions, I successfully established a functioning database for login credentials. This was verified using the Android Studio Database Inspector tool, which displays database entries.
  
</details>

<details open>
  <summary>Proof of Functioning Database</summary>

  MM add photo
</details>
