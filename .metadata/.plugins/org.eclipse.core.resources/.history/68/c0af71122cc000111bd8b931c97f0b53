package cusine.restaurant.finder;

import android.app.Activity;
import android.os.Bundle;
import android.util.Log;
import android.widget.TextView;
import android.widget.RatingBar;

public class RestaurantDetailsDisplayerActivity extends Activity{
	
	public void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		RestaurantDetails restaurantDetails = null; 
		setContentView(R.layout.restaurantdetails);
		Bundle extras = getIntent().getExtras();
		restaurantDetails = (RestaurantDetails) extras.getSerializable("selectedrestaurant");
		TextView restaurantName = (TextView) findViewById(R.id.textViewRestaurantNamevalue);
		TextView restaurantAddress = (TextView) findViewById(R.id.textViewRestaurantAddressvalue);
		TextView restaurantRating = (TextView) findViewById(R.id.textViewRestaurantRatingvalue);
		RatingBar restaurantRatingBar = (RatingBar) findViewById(R.id.restaurantRatingBar);
		Log.i("Resto Name:::", String.valueOf(restaurantDetails.getRestaurant_name()));
		Log.i("Resto Rating:::", String.valueOf(restaurantDetails.getRating()));
		restaurantName.setText(restaurantDetails.getRestaurant_name());
		restaurantAddress.setText(restaurantDetails.getRestaurant_address());
		restaurantRating.setText(""+restaurantDetails.getRating());
		restaurantRatingBar.setRating((float) restaurantDetails.getRating());
	}

}
