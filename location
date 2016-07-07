//NSLocationWhenInUseUsageDescription and NSLocationAlwaysUsageDescription as strings to the info.plist file to get user permission for accessing his/her location.

import UIKit
import CoreLocation

class ViewController: UIViewController, CLLocationManagerDelegate {

    @IBOutlet var LatitudeLabel: UILabel!
    
    @IBOutlet var LongitudeLabel: UILabel!
    
    @IBOutlet var SpeedLabel: UILabel!
    
    @IBOutlet var AltitudeLabel: UILabel!
    
    @IBOutlet var CourseLabel: UILabel!
    
    
    @IBOutlet var AddressLabel: UILabel!
    
    var manage:CLLocationManager!
    
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
       
        manage = CLLocationManager()
        manage.delegate = self
        manage.desiredAccuracy = kCLLocationAccuracyBest
        manage.requestWhenInUseAuthorization()
        manage.startUpdatingLocation()
        
        
    }
    
    func locationManager(manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        
        print(locations)
        
        let userlocation:CLLocation = locations[0]
        self.LatitudeLabel.text = "\(userlocation.coordinate.latitude)"
        self.LongitudeLabel.text = "\(userlocation.coordinate.longitude)"
        self.CourseLabel.text = "\(userlocation.course)"
        self.SpeedLabel.text = "\(userlocation.speed)"
        self.AltitudeLabel.text = "\(userlocation.altitude)"
        
        
        CLGeocoder().reverseGeocodeLocation(userlocation) { (placemarks, error) in
            if (error != nil)
            {
                print(error)
            }
        else
            {
                if let p = placemarks?[0]
                    {

                             var subThoroughfare:String = ""
                    
                    if (p.subThoroughfare != nil) {
                        
                        subThoroughfare = p.subThoroughfare!
}
    
                
                    
                    self.AddressLabel.text = "\(subThoroughfare) \(p.thoroughfare!) \n \(p.locality!) \n \(p.administrativeArea!) \n \(p.subAdministrativeArea!) \n \(p.postalCode!) \n \(p.country!)"
                    
                }
 
                
                }
    
        
        
        
        }
 
        
    }
    
    
    
    

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }


}

