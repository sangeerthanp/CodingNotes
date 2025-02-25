**Makemy.java**

```java
import java.util.*;

public class Makemy extends IndigoService {
  public static void main(String[] args) {
    List<Flights> a = getFlight();

    for (Flights i : a) {
      System.out.println(i);
    }
  }
}

```

**IndigoService.java**

```java
import java.io.*;
import java.util.*;

public class IndigoService {

  public static List<Flights> getFlight() {
    List<Flights> lst = new LinkedList<Flights>();

    BufferedReader reader;
    try(BufferedReader br= new BufferedReader(new FileReader("flights.txt"))) {
      String line = br.readLine();
      while (line != null) {
        Flights flight = new Flights();
        String[] i = line.split(",");
        flight.setId(i[0]);
        flight.setName(i[1]);
        flight.setSc(i[2]);
        flight.setDes(i[3]);
        lst.add(flight);
        line = br.readLine();
      }
      br.close();
    } catch (Exception e) {
      System.out.println(e);
    }

    return lst;
  }
}

```


**Flights.java**

```java
public class Flights{
    private String id;
    private String name;
    private String sc;
    private String des;

    public String getId() {
        return id;
    }
    public void setId(String id) {
        this.id = id;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getSc() {
        return sc;
    }
    public void setSc(String sc) {
        this.sc = sc;
    }
    public String getDes() {
        return des;
    }
    public void setDes(String des) {
        this.des = des;
    }
    public String toString() {
        return "Flight ID: " + id + ", Name: " + name + ", Source: " + sc + ", Destination: " + des;
    }
}

```


**Flights.txt**

| 101, | i1, | cbe, | hyd |
| ---- | --- | ---- | --- |
| 102, | i2, | hyd, | cbe |


**O/P**

![[../../../Pasted image 20240825225726.png]]