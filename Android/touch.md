    public class MainActivity extends Activity implements OnTouchListener{
        
        StringBuilder builder = new StringBuilder();
        TextView textView;
        /** Called when the activity is first created. */
        @Override
        public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            //this.getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN, WindowManager.LayoutParams.FLAG_FULLSCREEN);
            textView = new TextView(this);
            textView.setText("Touch and drag (one finger only)!"); 
            textView.setOnTouchListener(this);
            setContentView(textView);
            //setContentView(R.layout.activity_main); 
        }
        
        
        @Override
        public boolean onCreateOptionsMenu(Menu menu) {
            getMenuInflater().inflate(R.menu.activity_main, menu);
            return true;
        }


        @Override
        public boolean onTouch(View v, MotionEvent event) {
            builder.setLength(0);
            switch (event.getAction()) { case MotionEvent.ACTION_DOWN:
            builder.append("down, ");
            break;
            case MotionEvent.ACTION_MOVE:
            builder.append("move, ");
            break;
            case MotionEvent.ACTION_CANCEL:
            builder.append("cancle, ");
            break;
            case MotionEvent.ACTION_UP:
            builder.append("up, ");
            break; }
            builder.append(event.getX()); builder.append(", "); 
            builder.append(event.getY()); String text = builder.toString();
            Log.d("TouchTest", text); 
            textView.setText(text);
            return true;
        }
    }
