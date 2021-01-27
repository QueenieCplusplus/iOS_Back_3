# iOS_Back_3
to do a iBeacon Sensor feature with sys notification when app is running in background


  ![](https://raw.githubusercontent.com/QueenieCplusplus/iOS_Back_3/main/thumbnail.png)


1. define K/V in info propert list.

  ![](https://raw.githubusercontent.com/QueenieCplusplus/iOS_Back_3/main/info_property_list.png)


2. code in ViewController.


        //
        //  ViewController.swift
        //  KatesIBeaconBLEapp
        //
        //  Created by KatesAndroid on 2021/1/27 PM2 :20 ~
        //

        import UIKit
        import CoreBluetooth
        import CoreLocation

        class ViewController: UIViewController, CLLocationManagerDelegate {

            let cllm = CLLocationManager()

            override func viewDidLoad() {
                super.viewDidLoad()
                // after nib.

                cllm.requestAlwaysAuthorization()
                cllm.delegate = self

                // search for Beacon's UUID, which is 20 bytes.
                let uuid = UUID(uuidString: "B9407F30-F5F8-466E-AFF9-25556B57FE6D")
                let region = CLBeaconRegion(uuid: uuid!, identifier: "Kates Region")

                // this app helps to detect info of nearby beacon device.
                // cllm.startRangingBeacons is deprecated.
                cllm.startMonitoring(for: region)

                // to know how many and what are they
                // matters with major, minor, accury
                //cllm.startRangingBeacons(satisfying: <#T##CLBeaconIdentityConstraint#>)

            }

            // when app running at background.
            // method below can be called.

            func locationManager(_ manager: CLLocationManager, didEnterRegion region: CLRegion) {
                print("Enter\(region.identifier)")
            }

            func locationManager(_ manager: CLLocationManager, didExitRegion region: CLRegion) {
                print("Exit\(region.identifier)")
            }


        }
        
      ref: https://medium.com/彼得潘的-swift-ios-app-開發問題解答集/swift-ibeacon-app-程式設計-cd89f59f735b


![](https://raw.githubusercontent.com/QueenieCplusplus/iOS_Back_3/main/iBeacon.png)
