

import java.io.FileNotFoundException;
import java.io.FileOutputStream;

import com.itextpdf.text.Document;
import com.itextpdf.text.DocumentException;
import com.itextpdf.text.PageSize;
import com.itextpdf.text.Paragraph;
import com.itextpdf.text.Rectangle;
import com.itextpdf.text.pdf.Barcode128;
import com.itextpdf.text.pdf.PdfWriter;

public class barcode {

 public static void main(String[] args) throws FileNotFoundException, DocumentException {

    Document document = new Document(new Rectangle(PageSize.A4));    
    PdfWriter writer = PdfWriter.getInstance(document, new FileOutputStream("D:\\workspace\\Test\\barcode\\Java4s_BarCode_128.pdf"));    

    document.open();
    
	  for(int i=0;i<30;i++)
	  {
		  document.add(new Paragraph("Vacus"));

		    Barcode128 code128 = new Barcode128();
		    code128.setGenerateChecksum(true);
		    code128.setCode("5A-C2-15-B1-01-6"+i);    

	    document.add(code128.createImageWithBarcode(writer.getDirectContent(), null, null));
	  }
    document.close();

    System.out.println("Document Generated...!!!!!!");
  }

}
