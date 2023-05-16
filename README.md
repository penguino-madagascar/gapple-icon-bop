# note: this tutorial was made solely on psych engine (u can do this on any engine if you modify the code n stuff)

## 0.4.2 and older

go to playstate and search for

<img width="586" alt="Screenshot 2023-03-14 at 12 35 50 PM" src="https://user-images.githubusercontent.com/92494313/225117417-cee11c21-7d7e-443d-aaf2-e861c6c60c32.png">

and swap it with

```
iconP1.centerOffsets();
iconP2.centerOffsets();

iconP1.updateHitbox();
iconP2.updateHitbox();
```

after that, search for

<img width="304" alt="Screenshot 2023-03-14 at 12 35 01 PM" src="https://user-images.githubusercontent.com/92494313/225117297-7432f712-779e-4f19-8414-80a7838702e3.png">

and replace it with this

```
if (curBeat % gfSpeed == 0) {
					curBeat % (gfSpeed * 2) == 0 ? {
						iconP1.scale.set(1.1, 0.8);
						iconP2.scale.set(1.1, 1.3);
		
						FlxTween.angle(iconP1, -15, 0, Conductor.crochet / 1300 * gfSpeed, {ease: FlxEase.quadOut});
						FlxTween.angle(iconP2, 15, 0, Conductor.crochet / 1300 * gfSpeed, {ease: FlxEase.quadOut});
					} : {
						iconP1.scale.set(1.1, 1.3);
						iconP2.scale.set(1.1, 0.8);
		
						FlxTween.angle(iconP2, -15, 0, Conductor.crochet / 1300 * gfSpeed, {ease: FlxEase.quadOut});
						FlxTween.angle(iconP1, 15, 0, Conductor.crochet / 1300 * gfSpeed, {ease: FlxEase.quadOut});
					}
		
					FlxTween.tween(iconP1, {'scale.x': 1, 'scale.y': 1}, Conductor.crochet / 1250 * gfSpeed, {ease: FlxEase.quadOut});
					FlxTween.tween(iconP2, {'scale.x': 1, 'scale.y': 1}, Conductor.crochet / 1250 * gfSpeed, {ease: FlxEase.quadOut});
		
					iconP1.updateHitbox();
					iconP2.updateHitbox();
				}
```
if you dont have "gfSpeed" then add it above health like this

<img width="162" alt="Screenshot 2023-03-14 at 12 16 03 PM" src="https://user-images.githubusercontent.com/92494313/225113259-e61e2dc4-d30f-41eb-84c3-13044b8b1c00.png">

```
public var gfSpeed:Int = 1;
```

and thats it! :D

# 0.5+

### quick note before i move on

replace healthicon.hx with this

https://www.mediafire.com/file/a1kyahbsirlggux/HealthIcon.hx/file

if you dont replace it, the icon bounce will look like this

https://user-images.githubusercontent.com/92494313/225106201-67e2140a-7b21-4d12-86f4-3d62d8c71d75.mov

if you dont know the difference, look at a gapple video and see if you can spot anything

## ok back to the main stuff

go to playstate and search for

<img width="477" alt="Screenshot 2023-03-14 at 12 32 45 PM" src="https://user-images.githubusercontent.com/92494313/225116871-d701c229-94e4-46ab-a48c-78a2a35380bc.png">

and swap it with

```
iconP1.centerOffsets();
iconP2.centerOffsets();

iconP1.updateHitbox();
iconP2.updateHitbox();
```

after that, scroll down until you find

<img width="858" alt="Screenshot 2023-03-14 at 12 33 13 PM" src="https://user-images.githubusercontent.com/92494313/225117143-de7bc010-a220-4ded-bc73-7155a05ab8bc.png">

where you can swap it with

```
iconP1.x = healthBar.x + (healthBar.width * (FlxMath.remapToRange(healthBar.percent, 0, 100, 100, 0) * 0.01) - iconOffset);
		iconP2.x = healthBar.x + (healthBar.width * (FlxMath.remapToRange(healthBar.percent, 0, 100, 100, 0) * 0.01)) - (iconP2.width - iconOffset);
```

and then add in the stuff that i already talked about in the 0.4.2 section (u dont need to add in the gfspeed because it was already added)

and your done! :D
