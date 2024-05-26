# SI_2024_lab2_205002

Христина Ѓонеска, 205002

2.Control Flow Graph

CFG  е правено според вака поставени јазли

public class dmd {
    public class SILab2 {
        public static boolean checkCart(List<Item> allItems, int payment){
            if (allItems == null){//1
                throw new RuntimeException("allItems list can't be null!");//2
            }

            float sum = 0;//



            for (int i = 0; i < allItems.size(); i++){//3
                Item item = allItems.get(i);
                if (item.getName() == null || item.getName().length() == 0){//4
                    item.setName("unknown");//5
                }
                if (item.getBarcode() != null){//6
                    String allowed = "0123456789";
                    char chars[] = item.getBarcode().toCharArray();//
                    for (int j = 0; j < item.getBarcode().length(); j++){//7
                        char c = item.getBarcode().charAt(j);
                        if (allowed.indexOf(c) == -1){//8
                            throw new RuntimeException("Invalid character in item barcode!");//9
                        }
                        //7.3
                    }
                    if (item.getDiscount() > 0){//10
                        sum += item.getPrice()*item.getDiscount();//11
                    }
                    else {//12
                        sum += item.getPrice();
                    }
                }
                else {//13
                    throw new RuntimeException("No barcode!");
                }
                if (item.getPrice() > 300 && item.getDiscount() > 0 && item.getBarcode().charAt(0) == '0'){//14
                    sum -= 30;//15
                }
                //3.3
            }
            if (sum <= payment){//16
                return true;//17
            }
            else {
                return false;//18
            }
        }//19
    }
}



