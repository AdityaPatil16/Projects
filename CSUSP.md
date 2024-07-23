# Projects
# Front Screen

package myproject;

import java.awt.Button;
import java.awt.Color;
import java.awt.Font;
import java.awt.Frame;
import java.awt.Graphics;
import java.awt.Label;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;
import java.sql.SQLException;

import javax.imageio.ImageIO;


public class FrontScreen extends Frame implements ActionListener {
 
	
	BufferedImage bi;
	public static Label data;
	public static Label farmer;
	public static Button btnData;
	public static Button btnFarmer;
	public static Label lblHeading;
	public static Font ft;
	public static Font ft1;
	public static Font ft2;
	public FrontScreen()
	{
         setTitle("Main Screen");
		
		try {
			bi=ImageIO.read(new File("D:\\image1.jpg"));
		} catch (IOException e1) {
			
			e1.printStackTrace();
		}
		setSize(1800,900);
		
		setLayout(null);
		addWindowListener(new WindowAdapter()
		{
			public void windowClosing(WindowEvent e)
			{
				dispose();
				setVisible(false);
			}
			
		});
		
		lblHeading = new Label("CROP SUITABILITY USING SOIL PARAMETERS");
		add(lblHeading);
		lblHeading.setBounds(160, 150, 910, 35);
		ft = new Font("Arial",Font.CENTER_BASELINE,40);
		lblHeading.setFont(ft);
		lblHeading.setBackground(Color.orange);
		
		data = new Label("To insert values in database :");
		data.setBounds(90, 500, 285, 30);
		data.setBackground(Color.YELLOW);
		ft1 = new Font("Arial",Font.CENTER_BASELINE,20);
		data.setFont(ft1);
		
		btnFarmer = new Button ("Click Here");
		btnFarmer.setBounds(170, 550, 90, 30);
		
		farmer = new Label("To know Suitability of Crops :");
		farmer.setBounds(90, 300, 285, 30);		
		farmer.setFont(ft1);
		farmer.setBackground(Color.YELLOW);
		
		btnData = new Button ("Click Here");
		btnData.setBounds(170, 350, 80, 30);
		btnData.addActionListener(this);
		btnFarmer.addActionListener(this);
		add(data);
		add(farmer);
		add(btnFarmer);
		add(btnData);
	}
	
	public void paint(Graphics g)
    {
    	super.paint(g);
    	g.drawImage(bi,0, 0,getWidth(), getHeight(), null);
    }
	
	public static void main (String[] args){
		
          FrontScreen fs =  new FrontScreen();
          fs.show();
	}
	 
	public void actionPerformed(ActionEvent e) {
		
		if(e.getSource()==btnData)
		 {
			InputScreen input = new InputScreen();
			 input.show();
			 
			 
		 }
		 if(e.getSource()==btnFarmer)
		 {
			IdPass ip = new IdPass();
			ip.show();
		 }
		 
	}

}
