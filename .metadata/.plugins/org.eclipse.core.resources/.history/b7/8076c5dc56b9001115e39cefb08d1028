package hello.ui.project;

import android.app.Activity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class HelloUIProjectActivity extends Activity {
	/** Called when the activity is first created. */
	Button btnGreet;
	Button switchGreet;
	Intent intent;
	
	@Override
	public void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.main);
		btnGreet = (Button) findViewById(R.id.btnGreet);
		btnGreet.setOnClickListener(new OnClickListener() {
			public void onClick(View v) {
				// TODO Auto-generated method stub
				EditText enterName = (EditText) findViewById(R.id.edittxtEnterName);
				TextView showGreet = (TextView) findViewById(R.id.txtviewShowGreet);
				showGreet.setText("Hello " + enterName.getText() + " !");
			}
		});
		
		switchGreet = (Button) findViewById(R.id.btnSwitchGreet);
		switchGreet.setOnClickListener(new OnClickListener() {
			public void onClick(View v) {
				// TODO Auto-generated method stub
				intent = new Intent(HelloUIProjectActivity.this, SendoffActivity.class);
				startActivity(intent); 
			}
		});
	}
}