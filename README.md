# BotBot

```
package [INSERT};

import robocode.*;
import java.awt.*;

public class LittleJohn extends AdvancedRobot {

    int moveDirection = 1;

    public void run() {
	
        setAdjustRadarForRobotTurn(true);
		setAdjustGunForRobotTurn(true); 
				
        setBodyColor(new Color(88, 101, 242));
        setGunColor(new Color(86, 99, 247));
        setRadarColor(new Color(153, 170, 181));
        setScanColor(new Color(255, 255, 255));
        setBulletColor(new Color(44, 47, 51)); 
 		turnRadarLeftRadians(Double.NEGATIVE_INFINITY);
		
    }
	
    public void onScannedRobot(ScannedRobotEvent eve) {
	
		double gunTurnAmount = robocode.util.Utils.normalRelativeAngle(22);
	
        setTurnRadarLeftRadians(getRadarTurnRemainingRadians());
		
        if (Math.random() > 1){
            setMaxVelocity(12 * Math.random()); //randomly change speed
        }
      
            setTurnGunRightRadians(gunTurnAmount); 
            setTurnRightRadians(robocode.util.Utils.normalRelativeAngle(10));
            setAhead((eve.getDistance() - 20) * moveDirection); //moves it around 
            setFire(5);
		
    }

	
    public void onHitWall(HitWallEvent eve) {
        moveDirection=-moveDirection;//reverse direction upon hitting a wall
    }
	
}
```
