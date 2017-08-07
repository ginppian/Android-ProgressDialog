Android: Progress Dialog
==========

## Definición

<p align="justify">
A pesar de ser <i>DEPRECATE</i> es me muy útil.
</p>

```java
    private ProgressDialog progress;
    
    private void userValidation(){

        // Start progress UI
        progress = new ProgressDialog(MainActivity.this);
        progress.setIndeterminate(true);
        progress.setMessage("Autenticando...");
        progress.show();

        final Thread t = new Thread() {
            @Override
            public void run() {

                // Get value
                String correo = inputPerfil.getText().toString();
                String password = inputPass.getText().toString();

                // Login
                loginSinAsync(correo, password);

                // Stop progress
                progress.dismiss();

                // Change Activity
                if(authorize){

                    try{

                        //Intent intent = new Intent(MainActivity.this, Ubicacion.class);
                        Intent intent = new Intent(MainActivity.this, MapsActivity.class);
                        intent.putExtra("miCorreo", correo);
                        intent.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);
                        intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
                        startActivity(intent);
                        finish();

                    }catch(Exception e){
                        Log.d("what",e.getMessage());
                    }
                }
            }
        };
        t.start();
    }
```

## Fuente

* <a href="https://www.tutorialspoint.com/android/android_progressbar.htm">Android Progress Bar using ProgressDialog</a>