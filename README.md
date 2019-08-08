# teste
public class MainActivity extends AppCompatActivity {
    private DatabaseReference databaseReference = FirebaseDatabase.getInstance().getReference();
    Button btJogar;
    EditText edtNome;
    TextView recorde1;
    TextView recorde2;
    TextView recorde3;
    TextView nome1;
    TextView nome2;
    TextView nome3;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        getSupportActionBar().hide();
        setContentView(R.layout.activity_main);
        recorde1 = findViewById(R.id.txtRec1);
        recorde2 = findViewById(R.id.txtRec2);
        recorde3 = findViewById(R.id.txtRec3);
        nome1 = findViewById(R.id.txtNome1);
        nome2 = findViewById(R.id.txtNome2);
        nome3 = findViewById(R.id.txtNome3);
        edtNome = findViewById(R.id.edtNome);
        btJogar = findViewById(R.id.btJogar);



                btJogar.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                DatabaseReference recordes = databaseReference.child("recordes");
                Recorde recorde = new Recorde();


                recorde.setNome(edtNome.getText().toString());
                recorde.setUuid(UUID.randomUUID().toString());
                recordes.child(recorde.getUuid()).setValue(recorde);

                //recordes.setValue(recorde);

                Intent intent = new Intent(getApplicationContext(), JogoActivity.class);
                startActivity(intent);

            }
        });


    }


    }
    
    Na outra Activty 
    
    
                DatabaseReference recordes = databaseReference.child("recordes");
                Recorde recorde = new Recorde();
                recorde.setPontuacao(vitoriasN);
                recordes.child(recorde.getUuid()).setValue(recorde);
