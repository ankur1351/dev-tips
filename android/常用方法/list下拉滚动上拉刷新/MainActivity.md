
````java

package com.example.hello;

import java.util.ArrayList;

import com.example.hello.adapter.MyFragmentPagerAdaptert;
import com.example.hello.fragment.MyFragment;
import com.example.hello.fragment.myListFragment;
import com.example.hello.model.Person;

import android.R.string;
import android.annotation.TargetApi;
import android.app.ActionBar;
import android.app.Activity;
import android.app.AlertDialog;
import android.app.Notification;
import android.app.NotificationManager;
import android.app.PendingIntent;
import android.app.TabActivity;
import android.content.Context;
import android.content.DialogInterface;
import android.content.DialogInterface.OnClickListener;
import android.content.Intent;
import android.graphics.Color;
import android.net.Uri;
import android.os.Build;
import android.os.Bundle;
import android.support.v4.app.Fragment;
import android.support.v4.app.FragmentActivity;
import android.support.v4.view.ViewPager;
import android.text.TextUtils;
import android.view.ContextMenu;
import android.view.Gravity;
import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuItem;
import android.view.SubMenu;
import android.view.View;
import android.view.ContextMenu.ContextMenuInfo;
import android.webkit.JavascriptInterface;
import android.webkit.WebSettings;
import android.webkit.WebView;
import android.webkit.WebViewClient;
import android.widget.ArrayAdapter;
import android.widget.ImageView;
import android.widget.ListView;
import android.widget.SearchView;
import android.widget.SearchView.OnQueryTextListener;
import android.widget.TabHost;
import android.widget.TextView;
import android.widget.Toast;

public class TestActivity extends FragmentActivity {

	ViewPager viewPager ;
	int i = 0;

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_test);
		//user code
		initFragment();
	}
	private void initFragment() {
		 ArrayList<Fragment> fragments = new ArrayList<Fragment>();
		 Fragment fragment1 = new MyFragment("fragment1");
		 Fragment fragment2 = new myListFragment();
		 Fragment fragment3 = new MyFragment("fragment3");
		 fragments.add(fragment1);
		 fragments.add(fragment2);
		 fragments.add(fragment3);
		 
		MyFragmentPagerAdaptert adapter = 
				new MyFragmentPagerAdaptert(getSupportFragmentManager(),fragments);
		viewPager = (ViewPager) findViewById(R.id.viewPager);
		viewPager.setAdapter(adapter);
 
	}
	public void changPage(View view) {
		viewPager.setCurrentItem(i++%3);
	}
	 
}
````