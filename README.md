# AndroidTemelleri
temel Bilgiler

package example.com.siteyeyonlendirme;

import android.content.Intent;
import android.graphics.Color;
import android.net.Uri;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import org.w3c.dom.Text;

import java.util.Calendar;
import java.util.Random;

public class MainActivity extends AppCompatActivity {
    private int sayac1  = 0;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        final TextView t, sayac;

        Button arti, eksi;
        arti = (Button) findViewById(R.id.angry_btn);
        eksi = (Button) findViewById(R.id.angry_btn2);
        sayac = (TextView) findViewById(R.id.sayac);
        t = (TextView) findViewById(R.id.site);
        t.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent intent = new Intent(Intent.ACTION_VIEW);
                intent.setData(Uri.parse("http://www.diyetdoktorum.com"));
                startActivity(intent);
            }
        });

        arti.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                ++sayac1;
                sayac.setText(String.format("Kac kere Tikandi : %d", sayac1));


                // Her tıklayınca Bir nesnenin Arka Plan rengini değiştirmek.
                Random rnd= new Random();
                sayac.setBackgroundColor(Color.rgb(rnd.nextInt(255),rnd.nextInt(255),rnd.nextInt(255)));
            }
        });

        eksi.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
            --sayac1;
                sayac.setText(String.format("Kac kere Tikandi : %d", sayac1));


            }
        });


    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();

        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }

        return super.onOptionsItemSelected(item);
    }
}
