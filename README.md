# Examen_Unidad1

import javax.swing.*;
import javax.swing.border.Border;
import javax.swing.border.TitledBorder;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class Avionjimmy extends JFrame{

    //Declarar Button
    private  JButton buttonl;
    private  JButton buttonRe;
    private  JButton buttonOp1;
    private  JButton buttonP;
    private  JButton buttonOp2;
    private  JButton buttonB;

    //Declarar vector de JPanels de Asientos VIP
    private JButton[] asientosVIP;
    private JButton[] asientosNormales;
    //   Asientos vip

    private  JButton AV1;
    private  JButton AV2;
    private  JButton AV3;
    private  JButton AV4;
    private  JButton AV5;
    private  JButton AV6;
    private  JButton AV7;
    private  JButton AV8;


    public Avionjimmy(){

        super("Airline TZEK'S");

        //Botones principales
        JPanel ven1 = new JPanel();

        //Panel principal lado izquierdo
        JPanel ventanaIzq = new JPanel();

        //Panel principal lado derecho
        JPanel ventanaDerecha = new JPanel();

        //Parte VIP¨lado izq
        JPanel vent2= new JPanel();
        //Parte normal lado izq
        JPanel vent3 = new JPanel();
        //Parte VIP lado derecho
        JPanel vent4 = new JPanel();
        //Parte normal lado derecho
        JPanel vent5 = new JPanel();


        //  JLabel picture = new JLabel(new ImageIcon("src/avion.png"));

        asientosVIP = new JButton[8];
        asientosNormales = new JButton[42];
        //uso de botones principales
        buttonRe = new JButton("Registrar Pasajero");

        ven1.add(buttonRe);

        buttonl = new JButton("Eliminar Pasajero");
        ven1.add(buttonl);

        buttonB = new JButton("Buscar Pasajero");
        ven1.add(buttonB);

        buttonP = new JButton("Porcentaje de Ocupación");
        ven1.add(buttonP);

        buttonOp1 = new JButton("Opción 1");
        ven1.add(buttonOp1);

        buttonOp2 = new JButton("Opción 2");
        ven1.add(buttonOp2);

        int comprobacion = 0;
        int panelALlenar = 1;

        //Se crean los primeros asientos
        for(int i = 0; i<8;i++){
            if(panelALlenar == 1){
                asientosVIP[i] = new JButton(""+(i+1));
                vent2.add(asientosVIP[i]);
                comprobacion++;
            }else if(panelALlenar == 2){
                asientosVIP[i] = new JButton(""+(i+1));
                vent4.add(asientosVIP[i]);
                comprobacion++;
            }
            if(comprobacion == 2 && panelALlenar == 1){
                comprobacion = 0;
                panelALlenar = 2;
            }else if(comprobacion == 2 && panelALlenar == 2){
                comprobacion = 0;
                panelALlenar = 1;
            }
        }
        //Se crean los últimos asientos

        for(int i = 0; i<42;i++){
            if(panelALlenar == 1){
                asientosNormales[i] = new JButton(""+(i+9));
                vent3.add(asientosNormales[i]);
                comprobacion++;
            }else if(panelALlenar == 2){
                asientosNormales[i] = new JButton(""+(i+9));
                vent5.add(asientosNormales[i]);
                comprobacion++;
            }
            if(comprobacion == 3 && panelALlenar == 1){
                comprobacion = 0;
                panelALlenar = 2;
            }else if(comprobacion == 3 && panelALlenar == 2){
                comprobacion = 0;
                panelALlenar = 1;
            }
        }
        //JButton a = new JButton("asdasd");

        //vent4.add(a);

//color
        ven1.setBackground(Color.CYAN);
        ven1.setLayout(new GridLayout(2,3));
        ven1.setBorder(BorderFactory.createEmptyBorder(2,2,2,2));

        ventanaIzq.setBackground(Color.LIGHT_GRAY);
        ventanaIzq.setLayout(new GridLayout(2,1));
        ventanaIzq.setBorder(BorderFactory.createEmptyBorder(2,2,2,2));

        ventanaDerecha.setBackground(Color.LIGHT_GRAY);
        ventanaDerecha.setLayout(new GridLayout(2,1));
        ventanaDerecha.setBorder(BorderFactory.createEmptyBorder(2,2,2,2));

        ventanaIzq.add(vent2);
        ventanaIzq.add(vent3);
        ventanaDerecha.add(vent4);
        ventanaDerecha.add(vent5);

        vent2.setBackground(Color.GREEN);
        vent2.setLayout(new GridLayout(2,2));
        vent2.setBorder(BorderFactory.createEmptyBorder(2,2,2,2));

        vent3.setBackground(Color.LIGHT_GRAY);
        vent3.setLayout(new GridLayout(7,3));
        vent3.setBorder(BorderFactory.createEmptyBorder(2,2,2,2));


        vent4.setBackground(Color.GREEN);
        vent4.setLayout(new GridLayout(2,2));
        vent4.setBorder(BorderFactory.createEmptyBorder(2,2,2,2));

        vent5.setBackground(Color.LIGHT_GRAY);
        vent5.setLayout(new GridLayout(7,3));
        vent5.setBorder(BorderFactory.createEmptyBorder(2,2,2,2));



        //vent4.setBackground(Color.LIGHT_GRAY);
        //vent4.setLayout(new GridLayout(2,2));
        //vent4.setBorder(BorderFactory.createEmptyBorder(2,2,2,2));
        getContentPane().add(ven1,BorderLayout.NORTH);
        getContentPane().add(ventanaIzq,BorderLayout.WEST);
        getContentPane().add(ventanaDerecha,BorderLayout.EAST);


        //getContentPane().add(vent2,BorderLayout.WEST);
        //getContentPane().add(vent4,BorderLayout.WEST);
        //getContentPane().add(vent3,BorderLayout.EAST);
        //getContentPane().add(picture,BorderLayout.SOUTH);

        //acciones de botones
        ActionListener oyenteBtnReg =new ActionButtons();
        ActionListener oyenteBtnElim = new ActionButtons();
        ActionListener oyenteBtnBusc = new ActionButtons();
        ActionListener oyenteBtnO = new ActionButtons();
        ActionListener oyenteBtnO2= new ActionButtons();
        ActionListener oyenteBtnPor = new ActionButtons();

        //conecxión
        buttonRe.addActionListener(oyenteBtnReg);
        buttonl.addActionListener(oyenteBtnElim);
        buttonB.addActionListener(oyenteBtnBusc);
        buttonOp1.addActionListener(oyenteBtnO);
        buttonOp2.addActionListener(oyenteBtnO2);
        buttonP.addActionListener(oyenteBtnPor);

    }
    class ActionButtons implements ActionListener
    {
        @Override
        public void actionPerformed(ActionEvent e) {

            System.out.println("Presionaste el boton : "+((JButton)e.getSource()).getText());

            if (e.getSource() == buttonB)
            {
                JOptionPane.showMessageDialog(null,"Buscar Pasajero","Buscar",JOptionPane.PLAIN_MESSAGE);
            }
            else if (e.getSource() == buttonRe)
            {
                JOptionPane.showMessageDialog(null,"Registrar Pasajero","Registrar",JOptionPane.PLAIN_MESSAGE);
            }
            else if(e.getSource() == buttonl)
            {
                JOptionPane.showMessageDialog(null,"Eliminar Pasajero","Eliminar",JOptionPane.PLAIN_MESSAGE);
            }
            else if (e.getSource() == buttonP)
            {
                JOptionPane.showMessageDialog(null,"Porcentaje Ocupación","Porcentaje",JOptionPane.PLAIN_MESSAGE);
            }
            else if (e.getSource() == buttonOp1)
            {
                JOptionPane.showMessageDialog(null,"Opción 1","Option",JOptionPane.PLAIN_MESSAGE);
            }
            else if (e.getSource() == buttonOp2)
            {
                JOptionPane.showMessageDialog(null,"Opción 2","Option",JOptionPane.PLAIN_MESSAGE);
            }
        }
    }


    public static void main (String[]args) {
        Avionjimmy Aspirina = new Avionjimmy();
        Aspirina.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        Aspirina.pack();
        Aspirina.setLocation(500,30);
        Aspirina.setVisible(true);

    }


}
