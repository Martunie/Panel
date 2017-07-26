import java.awt.Dimension;
import java.awt.Graphics;
import java.awt.Graphics2D;
import java.awt.Image;
import java.awt.RenderingHints;
import java.awt.image.BufferedImage;
import java.awt.image.RescaleOp;
import java.io.File;
import java.io.IOException;
import java.net.MalformedURLException;
import java.net.URL;

import javax.imageio.ImageIO;
import javax.swing.ImageIcon;
import javax.swing.JPanel;


public class Panel extends JPanel {
 private BufferedImage netImage;
 private BufferedImage image;
 private int panelHeigth;
 private int panelWidth;
 
 Panel(){
	 super();
	 File imageFile=new File("mar.jpg");
	 

	 try {
		URL imageURL=new URL("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRPB_jV7oz6nE2I-hFpPquMwcJIqDM9rPtQc3Seqmefo4ldDTRS_A");
		netImage=ImageIO.read(imageURL);
		image=ImageIO.read(imageFile); 
	
	 } catch (IOException e) {
		System.err.println("Blad odczytu");
		e.printStackTrace();
	}
	 panelHeigth=netImage.getHeight()+image.getHeight();
	 panelWidth=netImage.getWidth()+image.getWidth();
	 Dimension dimension=new Dimension(panelWidth,panelHeigth);
	 setPreferredSize(dimension);
 }

 
 

@Override
 public void paintComponent(Graphics g){
	 Graphics2D g2d=(Graphics2D)g;
	 g2d.drawImage(netImage,0,0,null);
	 g2d.drawImage(image,netImage.getWidth(),0,null);
 }
 
 
 
