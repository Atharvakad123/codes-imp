import java.util.*;
class Appliance {
    protected int id;
    protected String name;
    protected boolean rented;
    
    public Appliance() {
    }

    public Appliance(int id, String name, boolean rented) {
        this.id = id;
        this.name = name;
        this.rented = rented;
    }
    
    public int getId() {
        return id;
    }
    
    public void setId(int id) {
        this.id = id;
    }
    
    public boolean getRented() {
        return rented;
    }
    
    public void setRented(boolean rented) {
        this.rented = rented;    
    } 
    
    public String toString() {
        return "Appliance{id=" + id + ", name='" + name +"', rented=" + rented + "} ";
    }
}
class ApplianceRentalSystem {
    protected ArrayList<Appliance> appList;
    protected int ctr;
    
    public ApplianceRentalSystem() {
        ctr = 301;
        appList = new ArrayList<>();
    }
    
    public void addAppliance(String name) {
        Appliance app = new Appliance(ctr, name, false);
        appList.add(app);
        ctr++;
    }

     public void rentAppliance(int id) {
         for(Appliance app : appList) {
             if(app.getId() == id) {
                app.setRented(true);
                System.out.println("Appliance with ID " + id +" is rented.");
                return;
             }
         }
        System.out.println("Appliance with ID " + id +" not found.");
     }    
     
    public void removeAppliance(int id) {
        for(int i = 0; i < appList.size(); i++) {
            Appliance app = appList.get(i);
            if(app.getId() == id) {
                appList.remove(id);
                System.out.println( "Appliance with ID " + id + " removed successfully." );
                return;
            }
        }
        System.out.println( "Appliance with ID " + id + " not found." );
    }
    
    public int coundNonRentedAppliance() {
        int ctr = 0;
        for(Appliance app : appList) {
            if(!app.getRented())
                ctr++;
        }
        return ctr;
    }
    
    public void displayAll() {
        for(Appliance app : appList)
            System.out.println(app);
    }
}
