# 3D_Investigadores-seg-n-sexo
//Tratando de girarlo

Table tabla;
PFont fuente;
PImage img;
PImage img2;


void setup() {
  size(1000, 700, P3D);
  img2= loadImage("color.png");
  background(img2);
}

void draw() {
  //img= loadImage("sim.png");
  camera(width/2, height/2, (height/2) / tan(PI/6), width/2, height/2, 0, 0, 1, 0);
  translate(0, 0, 0);
  background(img2);
  fuente = loadFont("AmericanTypewriter-Light-30.vlw");
 
  fill(255);
  textFont(fuente, 36);
  text("Becas Otorgadas para Maestría segun Sexo", 120, 650);
  textFont(fuente, 18);
  text("Hombres", 55, 45);
  text("Mujeres", 55, 75);
  //text("Investigadores según Sexo",900, 685);
  fill(255);
  rect(25, 25, 25, 25);
  fill(191, 50, 118);
  rect(25, 60, 25, 25);
 //image(img,240,65);
  tabla = loadTable("becas.csv", "header");

  println(tabla.getRowCount() + "filas en total en la tabla"); 

  camera(mouseX, height/2, (height/2) / tan(PI/6), width/2, height/2, 0, 0, 1, 0);
 
  for (TableRow row : tabla.rows ()) {

    int id = row.getInt("id");
    String nombre = row.getString("nombre");
    String apellido = row.getString("apellido");
    float edad = row.getFloat("edad");
    float promedio = row.getFloat("promedio");
    float diferencia = edad - promedio;

    println(nombre + " (" + apellido + ") tiene un id de " + id);

    fill(0);
    //text(id,50,50+(id*45));
    textFont(fuente, 18);
    text(nombre, 470, 100+(id*45));
    pushMatrix();

    rotateY(PI/4);
    translate(530, 85+(id*45));
    scale(1);
    noStroke();
    fill(255);
    rect(0, 0, 10+(edad*5), 20);
 
    rotateY(-PI/3);
    fill(191, 50, 118);
    rect(0, 0, 10-(promedio*5), 20);
    
    popMatrix();
  }
}
