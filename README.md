# Mapbox-SDK-Simple-Map
A simple map created using Xcode and the Mapbox SDK. Includes change of basemap style and popup markers on the map.

~~~~
import Mapbox

class ViewController: UIViewController, MGLMapViewDelegate {
    override func viewDidLoad() {
        super.viewDidLoad()
        
        // Set basemap style URL -- this one is called 'Scenic'
        let styleURL = URL(string: "mapbox://styles/apsmcd/cjem6a7uu1t3s2sqcstmxmmel")
        // Set map size properties and call style
        let mapView = MGLMapView(frame: view.bounds, styleURL: styleURL)
        mapView.autoresizingMask = [.flexibleWidth, .flexibleHeight]
        
        // Set the map’s center coordinate and zoom level.
        mapView.setCenter(CLLocationCoordinate2D(latitude: 50.609766, longitude: -4.183258), zoomLevel: 6, animated: false)
        view.addSubview(mapView)
        
        // Set the delegate property of our map view to `self` after instantiating it.
        mapView.delegate = self
        
        // Declare the marker `devon` and set its coordinates, title, and subtitle.
        let devon = MGLPointAnnotation()
        devon.coordinate = CLLocationCoordinate2D(latitude: 50.781493, longitude: -3.838385)
        devon.title = "Devon"
        devon.subtitle = "Where the jam goes on TOP of the clotted cream"
        
        // Declare the marker `cornwall` and set its coordinates, title, and subtitle.
        let cornwall = MGLPointAnnotation()
        cornwall.coordinate = CLLocationCoordinate2D(latitude: 50.380567, longitude: -4.922327)
        cornwall.title = "Cornwall"
        cornwall.subtitle = "Where the jam goes BENEATH the clotted cream"
        
        // Add marker `devon` to the map.
        mapView.addAnnotation(devon)
        
        // Add marker 'cornwall' to the map.
        mapView.addAnnotation(cornwall)
    }
    
    // Use the default marker. See also: our view annotation or custom marker examples.
    func mapView(_ mapView: MGLMapView, viewFor annotation: MGLAnnotation) -> MGLAnnotationView? {
        return nil
    }
    
    // Allow callout view to appear when an annotation is tapped.
    func mapView(_ mapView: MGLMapView, annotationCanShowCallout annotation: MGLAnnotation) -> Bool {
        return true
    }
}
~~~~
