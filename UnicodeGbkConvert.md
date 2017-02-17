	
		
	/**
	 * 
	 * @author norwaya	
 *
	 */
	public class Demo01 {
	
		public static void main(String[] args) {
			String text = "\\u5f00\\u59cb\\u4efb\\u52a1";
			String u2g = Demo01.unicodeToGbk(text);
			System.out.println(u2g);
			System.out.println(Demo01.GbkToUnicode(u2g));
		}

		public static String unicodeToGbk(String unicodeText) {
			Pattern p = Pattern.compile("[u][\\w]{4}");
			Matcher m = p.matcher(unicodeText);
			StringBuilder sbu = new StringBuilder();
			while (m.find()) {
				String str = m.group();
				sbu.append((char) (Integer.parseInt(str.substring(1), 16)));
			}
			return sbu.toString();
		}

		public static String GbkToUnicode(String gbk) {
			StringBuilder sbu = new StringBuilder();
			for (char c : gbk.toCharArray()) {
				sbu.append("\\u").append(Integer.toHexString(c));
			}
			return sbu.toString();
		}
	}
