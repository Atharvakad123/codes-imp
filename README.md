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
                appList.remove(i);
                System.out.println( "Appliance with ID " + id + " removed successfully." );
                return;
            }
        }
        System.out.println( "Appliance with ID " + id + " not found." );
    }
    
    public int countNonRentedAppliance() {
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
class Main {
    public static void main(String args[]) {
        ApplianceRentalSystem ars = new ApplianceRentalSystem();
        Scanner obj = new Scanner(System.in);
        int size = obj.nextInt();
        obj.nextLine();
        for(int i = 0; i < size; i++)
            ars.addAppliance(obj.nextLine());
        int rentApplianceId = obj.nextInt();
        int removeApplianceId = obj.nextInt();
        System.out.println("Appliances in the Inventory: ");
        ars.displayAll();
        ars.rentAppliance(rentApplianceId);
        ars.removeAppliance(removeApplianceId);
        System.out.println("Updated Inventory:");
        ars.displayAll();
        int total = ars.countNonRentedAppliance();
        System.out.println("Total non-rented appliances: " + total); 
        obj.close();
    }
}
