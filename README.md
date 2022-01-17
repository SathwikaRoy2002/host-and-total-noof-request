import java.io.*;
import java.util.*;
import java.util.regex.*;

public class Solution {
    private static final Scanner scan = new Scanner(System.in);
    
    public static void main(String args[]) throws Exception {
        // read the string filename
        String filename;
        filename = scan.nextLine();
        
        Scanner sc = new Scanner(new File(filename));
        
        HashMap<String,Integer> map= new HashMap<>();
        
        while(sc.hasNextLine()){
            String str = sc.nextLine();
            StringBuilder s = new StringBuilder();
            for(int i=0;i<str.length();i++){
                char ch = str.charAt(i);
                if(ch==' ') break;
                s.append(ch);
            }
            String host = s.toString();
            if(map.containsKey(host)){
                int val = map.get(host);
                map.put(host, val+1);
            }else{
                map.put(host, 1);
            }
        }
        
        BufferedWriter writer = new BufferedWriter(new FileWriter("records_"+filename));
        
        for(Map.Entry<String,Integer> entry:map.entrySet()){
            writer.write(entry.getKey()+" "+entry.getValue().toString());
            writer.newLine();
        }
        writer.close();
    }
}
