# Java-Event-Track

## Original Project

<details open>
  <summary>Create Account Screen</summary>

  ![Original Scene](https://github.com/melcian404/melcian404.github.io/blob/main/docs/assets/CreateAccount.PNG)
  
</details>

<details>
  <summary>Project Description</summary>

The origin of this school project is to create an Event-Tracking app that stores dates and times of upcoming events by allowing users to enter event details. The app displays events on the home screen in a grid view format. Users can add, remove, and edit event details. Data is stored in two database tables, one for login information and the other for event data. This project demonstrates my ability to create a locally stored SQLite database on Android. This project was completed initially using Java with Android Studio on 12/15/24.

My ePortfolio included this because it will demonstrate my skills in full-stack development and databases with the Java Programming Language. It also shows my ability to use the Android Studio IDE for mobile app development and UI/UX best practices, including screen optimization, accessibility, and app flow. This will align with creating a login requirement to prevent potential vulnerabilities and ensure privacy and security.

</details>

## Enhanced Project

<details>
  <summary>
    Enhancement Plan
  </summary> 
When first creating this project, I spent too much time designing the UI and didn’t end up with a fully functioning project. It incorporated the beginning of a database, but it was very rudimentary and non-functional. It was disappointing not to have a finished product when I was so excited about this project. With this enhancement, I’d like to get the user databases working properly. It would be the easiest route to scrap my prior user database entirely and start fresh. This will require stripping and recreating the UserDB class, then editing the MainActivity.
</details>

<details>
  <summary>Enhancements Completed</summary>
  
-	Remake the entire app with better inline comments.
-	Create a functioning database for users to create an account.
-	Verify database was established. 
  
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

  ![Original Scene](https://github.com/melcian404/melcian404.github.io/blob/main/docs/assets/ConfirmedDB.PNG)
  
</details>
