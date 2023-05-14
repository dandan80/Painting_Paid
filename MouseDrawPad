import java.awt.*;
import java.awt.event.*;
import java.awt.image.BufferedImage;

import javax.swing.*;

public class Number {
	
	private Frame frame = new Frame("Freehand Program");
    
	// DrawArea's size
	private final int AREA_WIDTH = 500;
	private final int AREA_HEIGHT = 400;
	
	//right-click menu
	private PopupMenu colorMenu = new PopupMenu();
	private MenuItem redItem = new MenuItem("red");
	private MenuItem greenItem = new MenuItem("green");
	private MenuItem blueItem = new MenuItem("blue");
	
	// current color that user choice to draw
	private Color forceColor =  Color.BLACK;
	
	// create a BufferedImage instance
	BufferedImage image = new BufferedImage(AREA_WIDTH, AREA_HEIGHT, BufferedImage.TYPE_INT_RGB);
	
	//create a Graphics instance
	Graphics g= image.getGraphics();
	
    //create a class inherit Canvas
	private class MyCanvas extends Canvas{
		
	@Override
		public void paint(Graphics g) {
			// TODO Auto-generated method stub
			g.drawImage(image, 0,0,null);
		}
	}
	
    MyCanvas drawArea = new MyCanvas();
    
    // variables used to record coordinate of mouse motion
    private int preX=-1;
    private int preY=-1;
	public void init() {
		
        ActionListener listener = new ActionListener() {

			@Override
			public void actionPerformed(ActionEvent e) {
				// TODO Auto-generated method stub
				String actionCommand = e.getActionCommand();
				switch(actionCommand) {
				case "red": 
					forceColor = Color.red;
					break;
				case "green":
					forceColor = Color.GREEN;
					break;
				case "blue":
					forceColor = Color.blue;
					break;
				}
			} 	
        };
        
        redItem.addActionListener(listener);
        greenItem.addActionListener(listener);
        blueItem.addActionListener(listener);
        
        colorMenu.add(redItem);
        colorMenu.add(greenItem);
        colorMenu.add(blueItem);
        
        //add colorMenu to drawArea
        drawArea.add(colorMenu);
        
        drawArea.addMouseListener(new MouseAdapter() {

			@Override
			public void mouseReleased(MouseEvent e) {
				// TODO Auto-generated method stub
				boolean popupTrigger = e.isPopupTrigger();
				if(popupTrigger) {
					colorMenu.show(drawArea, e.getX(), e.getY());
				}
				preX = -1;
				preY = -1;
			}
        });
        
        
        // set background color white
        g.setColor(Color.WHITE);
        g.fillRect(0, 0, AREA_WIDTH, AREA_HEIGHT);
        
        //create listener about mouse motion to draw lines in draw area
        drawArea.addMouseMotionListener(new MouseMotionAdapter() {

			@Override
			public void mouseDragged(MouseEvent e) {
				if(preX > 0 && preY > 0) {
				// TODO Auto-generated method stub
					g.setColor(forceColor);
					
				g.drawLine(preX, preY, e.getX(), e.getY());
				}
				//renew coordinate of pre-position
				preX = e.getX();
				preY = e.getY();
				
				drawArea.repaint();
			}
        	
        });
        
        drawArea.setPreferredSize(new Dimension(AREA_WIDTH, AREA_HEIGHT));
        frame.add(drawArea);
		frame.pack();
		frame.setVisible(true);
	}
	public static void main(String []args) {
		new Number().init();
	}
}
