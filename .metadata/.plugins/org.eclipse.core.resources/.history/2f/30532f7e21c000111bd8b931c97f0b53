package cusine.restaurant.finder;

import java.io.IOException;
import java.util.ArrayList;
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

public class RestaurantListDisplayerActivity extends ListActivity{
	
	RestClient restClient = new RestClient();
	String json;
	JSONArray restaurantsArray = null;
	//JSONParser jParser = new JSONParser();
	private static final String TAG_RESULTS = "results";
	private static final String TAG_RESULT = "result";
	private static final String TAG_RESTAURANTNAME = "name";
	private static final String TAG_RESTAURANTADDRESS = "address";
	private static final String TAG_RESTAURANTID = "id";
	private static final String TAG_RESTAURANTRATING = "rating_editor_overall";
	int cuisine_id;
    
	

	@Override
	public void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.restaurants);
		//TextView showName = (TextView) findViewById(R.id.txtViewShowJSON);
		Bundle extras = getIntent().getExtras();
		cuisine_id= extras.getInt("cuisine_id");
		List<NameValuePair> nameValuePairs = new ArrayList<NameValuePair>(1);
		nameValuePairs.add(new BasicNameValuePair("apikey", "4fd09cc934aa62322962394fd09cc934"));
		nameValuePairs.add(new BasicNameValuePair("city_id", "5"));
		nameValuePairs.add(new BasicNameValuePair("cuisine_id", ""+cuisine_id));
		try {
			json = restClient.doApiCall("search.json", "GET", nameValuePairs);
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
			JSONObject jsonRestaurants = new JSONObject(json);
			Log.i("json::::::::::", String.valueOf(jsonRestaurants));
			restaurantsArray = jsonRestaurants.getJSONArray(TAG_RESULTS);
			//System.out.println(""+json);

			ArrayList<RestaurantDetails> contactList = new ArrayList<RestaurantDetails>();
			for(int i = 0; i < restaurantsArray.length(); i++){
				JSONObject cuisine = restaurantsArray.getJSONObject(i);	
				JSONObject specificrestaurant = cuisine.getJSONObject(TAG_RESULT);
				String restaurantname = specificrestaurant.getString(TAG_RESTAURANTNAME);
				String restaurantaddress = specificrestaurant.getString(TAG_RESTAURANTADDRESS);
				int restaurantid = specificrestaurant.getInt(TAG_RESTAURANTID);
				double restaurantrating = specificrestaurant.getInt(TAG_RESTAURANTRATING);
				RestaurantDetails restaurantDetails = new RestaurantDetails();
				restaurantDetails.setId(restaurantid);
				restaurantDetails.setRating(restaurantrating);
				restaurantDetails.setRestaurant_address(restaurantaddress);
				restaurantDetails.setRestaurant_name(restaurantname);
				contactList.add(restaurantDetails);
				//System.out.println(""+name);

			}

			ArrayAdapter<RestaurantDetails> adapter = new ArrayAdapter<RestaurantDetails>(this,
					android.R.layout.simple_list_item_1, contactList);
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
		RestaurantDetails selectedrestaurant = (RestaurantDetails) getListAdapter().getItem(position);
		// Starting new intent
		Intent intent = new Intent(RestaurantListDisplayerActivity.this, RestaurantDetailsDisplayerActivity.class);
		intent.putExtra("selectedrestaurant", selectedrestaurant);
		startActivity(intent);
	}

	

}
