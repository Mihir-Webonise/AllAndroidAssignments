package cusine.restaurant.finder;

import java.io.IOException;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;

import org.apache.http.NameValuePair;
import org.apache.http.client.ClientProtocolException;
import org.apache.http.message.BasicNameValuePair;
import org.json.JSONArray;
import org.json.JSONException;
import org.json.JSONObject;

import android.app.ListActivity;
import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.ArrayAdapter;
import android.widget.ListView;

public class NewZomatoAssignmentActivity extends ListActivity {
	/** Called when the activity is first created. */
	RestClient restClient = new RestClient();
	String json;
	JSONArray cuisines = null;
	//JSONParser jParser = new JSONParser();
	private static final String TAG_CUISINES = "cuisines";
	private static final String TAG_CUISINE = "cuisine";
	private static final String TAG_CUISINENAME = "cuisine_name";
	private static final String TAG_CUISINEID = "cuisine_id";

	@Override
	public void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.zomato);
		//TextView showName = (TextView) findViewById(R.id.txtViewShowJSON);
		List<NameValuePair> nameValuePairs = new ArrayList<NameValuePair>(1);
		nameValuePairs.add(new BasicNameValuePair("apikey", "4fd09cc934aa62322962394fd09cc934"));
		nameValuePairs.add(new BasicNameValuePair("city_id", "5"));
		try {
			json = restClient.doApiCall("cuisines.json", "GET", nameValuePairs);
			Log.i("json::::::::::", String.valueOf(json));
			//String stringUrl = "https://api.zomato.com/v1/cuisines.json?apikey=4fd09cc934aa62322962394fd09cc934&city_id=5";
			//json = restClient.getResponseText(stringUrl);
		} catch (ClientProtocolException e) {
			// TODO Auto-generated catch block
			//e.printStackTrace();
			Log.i("ClientProtocolException::::::::::", String.valueOf(e));
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
			Log.i("IOException::::::::::", String.valueOf(e));
		}

		try {
			//JSONObject jsonCuisines = restClient.getJSONFromUrl("https://api.zomato.com/v1/cuisines.json?apikey=4fd09cc934aa62322962394fd09cc934&city_id=5");
			JSONObject jsonCuisines = new JSONObject(json);
			Log.i("json::::::::::", String.valueOf(jsonCuisines));
			cuisines = jsonCuisines.getJSONArray(TAG_CUISINES);
			//System.out.println(""+json);

			ArrayList<Cuisines> cuisinesList = new ArrayList<Cuisines>();
			//ArrayList<HashMap<String, String>> cuisinesDetailsList = new ArrayList<HashMap<String, String>>();
			 
			for(int i = 0; i < cuisines.length(); i++){
				JSONObject cuisine = cuisines.getJSONObject(i);	
				JSONObject specificcuisine = cuisine.getJSONObject(TAG_CUISINE);
				String cuisine_name = specificcuisine.getString(TAG_CUISINENAME);	
				int cuisine_id = Integer.parseInt(specificcuisine.getString(TAG_CUISINEID));
				Cuisines cuisines = new Cuisines();
				cuisines.setCuisine_id(cuisine_id);
				cuisines.setCuisine_name(cuisine_name);
				cuisinesList.add(cuisines);
				//System.out.println(""+name);

			}
			
			

			ArrayAdapter<Cuisines> adapter = new ArrayAdapter<Cuisines>(this,
					android.R.layout.simple_list_item_1, cuisinesList);
			setListAdapter(adapter);

			// selecting single ListView item
			// ListView lv = getListView();
		} catch (JSONException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		//showName.setText(" This is json "+json);
	}

	@Override
	public void onListItemClick(ListView l, View v, int position, long id) {
		// getting values from selected ListItem
		Cuisines selectedcuisine = (Cuisines) getListAdapter().getItem(position);
		// Starting new intent
		Intent intent = new Intent(NewZomatoAssignmentActivity.this, RestaurantListDisplayerActivity.class);
		intent.putExtra("cuisinename", selectedcuisine.getCuisine_name());
		intent.putExtra("cuisine_id", selectedcuisine.getCuisine_id());
		startActivity(intent);
	}


}