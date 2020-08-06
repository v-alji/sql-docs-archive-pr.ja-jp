---
title: Try ブロックと Catch ブロックの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a6aadb392fa4117484f3373ae232c3ed9c4b1d63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739216"
---
# <a name="using-try-and-catch-blocks"></a><span data-ttu-id="5c756-102">Try ブロックと Catch ブロックの使用</span><span class="sxs-lookup"><span data-stu-id="5c756-102">Using Try and Catch Blocks</span></span>
  <span data-ttu-id="5c756-103">条件ステートメントをコードに追加し、レポート サーバーに無効な要求が発行されないようにしたら、try ブロックと catch ブロックを使用して十分な例外処理を指定してください。</span><span class="sxs-lookup"><span data-stu-id="5c756-103">After you limit invalid requests to the report server by adding conditional statements to your code, you should supply adequate exception handling through the use of try/catch blocks.</span></span> <span data-ttu-id="5c756-104">これによって、レポート サーバーを無効な要求からさらに保護することができます。</span><span class="sxs-lookup"><span data-stu-id="5c756-104">This technique provides another layer of protection against requests that are not valid.</span></span> <span data-ttu-id="5c756-105">レポート サーバーへの要求を try ブロックに入れ、要求が原因でレポート サーバーが例外をスローしたときは、その例外を catch ブロックでキャッチすることで、アプリケーションが異常終了するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="5c756-105">If a request to the report server is encased in a try block and that request causes the report server to throw an exception, the exception is caught in the catch block, thus preventing your application from ending unexpectedly.</span></span> <span data-ttu-id="5c756-106">例外をキャッチしたら、例外を使用して別のことを実行するようにユーザーに指示することができます。または、エラーが発生したことだけをわかりやすくユーザーに通知することもできます。</span><span class="sxs-lookup"><span data-stu-id="5c756-106">Once the exception is caught, you can use the exception to either instruct the user to do something differently, or just let the user know, in a friendly way, that an error has occurred.</span></span> <span data-ttu-id="5c756-107">最終的には、ブロックを使用してすべてのリソースをクリーンアップできます。</span><span class="sxs-lookup"><span data-stu-id="5c756-107">You can then use a finally block to clean up any resources.</span></span> <span data-ttu-id="5c756-108">try ブロックや catch ブロックの不必要な重複を避けるために、汎用的な例外処理プランを生成することが理想的です。</span><span class="sxs-lookup"><span data-stu-id="5c756-108">Ideally, you should generate a general exception-handling plan to avoid unnecessary duplication of try/catch blocks.</span></span>  
  
 <span data-ttu-id="5c756-109">次の例では、try ブロックと catch ブロックを使用して例外処理コードの信頼性を高めています。</span><span class="sxs-lookup"><span data-stu-id="5c756-109">The following example uses try/catch blocks to enhance the reliability of the exception handling code.</span></span>  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c756-110">参照</span><span class="sxs-lookup"><span data-stu-id="5c756-110">See Also</span></span>  
 <span data-ttu-id="5c756-111">[Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="5c756-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="5c756-112">Reporting Services SoapException クラス</span><span class="sxs-lookup"><span data-stu-id="5c756-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
