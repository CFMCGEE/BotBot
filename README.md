# LittleJohnSenior
```
package pafighters;

import robocode.*;
import java.awt.*;

public class LittleJohnSenior extends AdvancedRobot {

    int moveDirection = 1;

    public void run() {
	
        setAdjustRadarForRobotTurn(true);
		setAdjustGunForRobotTurn(true); 

        setBodyColor(new Color(88, 101, 242));
        setGunColor(new Color(86, 99, 247));
        setRadarColor(new Color(153, 170, 181));
        setScanColor(new Color(255, 255, 255));
        setBulletColor(new Color(44, 47, 51)); 
        turnRadarRightRadians(Double.NEGATIVE_INFINITY);
		
    }

    public void onScannedRobot(ScannedRobotEvent e) {
	
        double absBearing = e.getBearingRadians()+getHeadingRadians();
        double latVel = e.getVelocity() * Math.sin(e.getHeadingRadians() -absBearing);
        double gunTurnAmount;
		
        setTurnRadarLeftRadians(getRadarTurnRemainingRadians());
       
		if (Math.random() > .12) {
            setMaxVelocity((12 * Math.random()) + 7);
        }
		
        if (e.getDistance() > 150) {
		
            gunTurnAmount = robocode.util.Utils.normalRelativeAngle(absBearing- getGunHeadingRadians() + latVel/22);
            setTurnGunRightRadians(gunTurnAmount); 
            setTurnRightRadians(robocode.util.Utils.normalRelativeAngle(absBearing-getHeadingRadians() + latVel/getVelocity()));
            setAhead((e.getDistance() - 140) * moveDirection);
            setFire(5);
			
        } else {
			
            gunTurnAmount = robocode.util.Utils.normalRelativeAngle(absBearing- getGunHeadingRadians() + latVel/15);
            setTurnGunRightRadians(gunTurnAmount); 
            setTurnLeft(-90 - e.getBearing()); 
            setAhead((e.getDistance() - 140) * moveDirection);
            setFire(5);
			
        }
    }
	
    public void onHitWall(HitWallEvent e){
        moveDirection = -moveDirection;
    }

}
```
