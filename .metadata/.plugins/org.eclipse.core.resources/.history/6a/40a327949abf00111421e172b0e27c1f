package cusine.restaurant.finder;

import java.util.ArrayList;
import java.util.List;

import android.content.ContentValues;
import android.content.Context;
import android.database.Cursor;
import android.database.SQLException;
import android.database.sqlite.SQLiteDatabase;
import android.util.Log;

public class CuisinesDataSource {

	private SQLiteDatabase database;
	private MySQLiteHelper dbHelper;
	private String[] allColumns = { MySQLiteHelper.COLUMN_CUISINE_ID,
			MySQLiteHelper.COLUMN_CUISINE_NAME };

	public CuisinesDataSource(Context context) {
		// TODO Auto-generated constructor stub
		dbHelper = new MySQLiteHelper(context);
	}

	public void open() throws SQLException {
		database = dbHelper.getWritableDatabase();
	}

	public void close() {
		dbHelper.close();
	}

	public Cuisines createCuisines(String cuisinename, int cuisineid) {
		ContentValues values = new ContentValues();
		values.put(MySQLiteHelper.COLUMN_CUISINE_ID, cuisineid);
		values.put(MySQLiteHelper.COLUMN_CUISINE_NAME, cuisinename);
		
		/*long insertId = database.insert(MySQLiteHelper.TABLE_CUISINES, null,
				values);*/
		Log.i("cuisine_id::::::::::", String.valueOf(cuisineid));
		Log.i("cuisine_name::::::::::", String.valueOf(cuisinename));
		/*String sql =   "INSERT INTO "+MySQLiteHelper.TABLE_CUISINES+
				" ("+MySQLiteHelper.COLUMN_CUISINE_ID+","+MySQLiteHelper.COLUMN_CUISINE_NAME+") " +
		        " VALUES (" + cuisineid + ", " + cuisinename + ")";
		*/
		//Log.v("Test Saving", sql);
		
		//database.rawQuery(sql, null);
		database.insert(MySQLiteHelper.TABLE_CUISINES, null, values);
		Cursor cursor = database.query(MySQLiteHelper.TABLE_CUISINES,
				allColumns, null, null, null, null, null);
		cursor.moveToFirst();
		Cuisines newComment = cursorToCuisines(cursor);
		cursor.close();
		return newComment;
	}

	public void deleteCuisines(Cuisines Cuisines) {
		int id = Cuisines.getCuisine_id();
		System.out.println("Cuisines deleted with id: " + id);
		database.delete(MySQLiteHelper.TABLE_CUISINES, MySQLiteHelper.COLUMN_CUISINE_ID
				+ " = " + id, null);
	}

	public List<Cuisines> getAllCuisiness() {
		List<Cuisines> Cuisiness = new ArrayList<Cuisines>();

		Cursor cursor = database.query(MySQLiteHelper.TABLE_CUISINES,
				allColumns, null, null, null, null, null);

		cursor.moveToFirst();
		while (!cursor.isAfterLast()) {
			Cuisines Cuisines = cursorToCuisines(cursor);
			Cuisiness.add(Cuisines);
			cursor.moveToNext();
		}
		// Make sure to close the cursor
		cursor.close();
		return Cuisiness;
	}

	private Cuisines cursorToCuisines(Cursor cursor) {
		Cuisines Cuisines = new Cuisines();
		Cuisines.setCuisine_id(cursor.getInt(0));
		Cuisines.setCuisine_name(cursor.getString(1));		
		return Cuisines;
	}


}

