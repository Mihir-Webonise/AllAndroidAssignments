package cusine.restaurant.finder;
import android.content.Context;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;
import android.util.Log;

public class MySQLiteHelper extends SQLiteOpenHelper {

	public static final String TABLE_CUISINES= "cuisines";
	public static final String TABLE_RESTAURANTS = "restaurants";
	public static final String COLUMN_CUISINE_ID = "_id";
	public static final String COLUMN_CUISINE_NAME = "cuisine_name";
    public static final String COLUMN_RESTAURANT_ID = "gender";
    public static final String COLUMN_RESTAURANT_NAME = "designation";
    public static final String COLUMN_RESTAURANT_ADDRESS = "location";
    public static final String COLUMN_RESTAURANT_RATING = "location";
    
	private static final String DATABASE_NAME = "empdb.db";
	private static final int DATABASE_VERSION = 1;

	// Database creation sql statement
	private static final String DATABASE_CREATE1 = "create table "
			+ TABLE_CUISINES + "(" + COLUMN_CUISINE_ID
			+ " integer primary key , " + COLUMN_CUISINE_NAME
			+ " text not null );";
	
	private static final String DATABASE_CREATE2 = "create table "
			+ TABLE_RESTAURANTS + "(" 
			+ COLUMN_RESTAURANT_ID + " integer primary key , "
			+ COLUMN_RESTAURANT_NAME + " text not null , "
			+ COLUMN_RESTAURANT_ADDRESS + " text not null , "
			+ COLUMN_RESTAURANT_RATING + " text not null "			
			+ ");";

	public MySQLiteHelper(Context context) {
		super(context, DATABASE_NAME, null, DATABASE_VERSION);
	}

	@Override
	public void onCreate(SQLiteDatabase database) {
		database.execSQL(DATABASE_CREATE1);
		database.execSQL(DATABASE_CREATE2);
	}

	@Override
	public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
		Log.w(MySQLiteHelper.class.getName(),
				"Upgrading database from version " + oldVersion + " to "
						+ newVersion + ", which will destroy all old data");
		db.execSQL("DROP TABLE IF EXISTS " + TABLE_CUISINES);
		onCreate(db);
	}
}
