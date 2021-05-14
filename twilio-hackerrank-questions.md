
```
import java.io.*;
import java.util.*;
import java.util.regex.*;

public class Solution {
    private static final Scanner scan = new Scanner(System.in);
    
    public static void main(String args[]) throws Exception {
        // read the string filename
        String filename;
        filename = scan.nextLine();
        
        String data = readFile(filename);
        String outputFile = "gifs_" + filename;
        OutputStream os = null;
        
        try{
            os = new FileOutputStream(new File(outputFile), true);
            os.write(data.getBytes(), 0, data.length());
        }
        catch(IOException ex){
            //
        }
        finally{
            try{
                os.close();
            }
            catch(IOException ex){
                //
            }
        }
    }
    
    static String readFile(String fileName) throws IOException{
        BufferedReader br = new BufferedReader(new FileReader(fileName));
        
        try{
            StringBuilder sb = new StringBuilder();
            
            String line = br.readLine();
            Set<String> unique = new HashSet<>();
            while(line != null){
                String[] temp = line.split(" ");
                String tempStr = temp[6];
                System.out.println(tempStr + " " + temp[5] + " " + temp[8]);
                //int responseCode = Integer.parseInt(temp[8]);
                
                String lastStr = tempStr.substring(tempStr.lastIndexOf("/") + 1);
                
                if(temp[5].contains("GET") && temp[8].equals("200") && (lastStr.contains(".gif") || lastStr.contains(".GIF"))){
                    if(!unique.contains(lastStr)){
                        sb.append(lastStr);
                        sb.append("\n");
                    }
                    unique.add(lastStr);
                }
                line = br.readLine();
            }
            //System.out.println(sb.toString());
            
            return sb.toString();
        } finally{
            br.close();
        }
    }
}
```

```
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;



class Result {

    /*
     * Complete the 'firstOccurrence' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts following parameters:
     *  1. STRING s
     *  2. STRING x
     */

    public static int firstOccurrence(String s, String x) {
        
        if(x.length() > s.length() || x.isEmpty() || s.isEmpty()){
            return -1;
        }
        
        int j = 0;
        int idx = -1;
        boolean check = false;
        
        for(int i=0;i<s.length();i++){
            if(j < x.length() && (s.charAt(i) == x.charAt(j) || x.charAt(j) == '*')){
                if(idx==-1){
                    idx=i;
                }
                check=true;
                j=j+1;
            }
            else if(check && j < x.length()){
                idx=-1;
                check=false;
                j=0;
            }
        }
        
        return idx;
    }
}
```
