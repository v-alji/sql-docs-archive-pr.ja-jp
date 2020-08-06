---
title: 無効な要求の回避 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 12343955c46fb98fea75048a38749b1db993fa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644305"
---
# <a name="preventing-invalid-requests"></a><span data-ttu-id="c83fb-102">無効な要求の回避</span><span class="sxs-lookup"><span data-stu-id="c83fb-102">Preventing Invalid Requests</span></span>
  <span data-ttu-id="c83fb-103">アプリケーション フローを分析し、レポート サーバーに送信される要求が有効であることを確認することによって、ある種類の例外がスローされないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="c83fb-103">You can prevent some types of exceptions from being thrown by analyzing your application flow and ensuring that the requests being sent to the report server are valid.</span></span> <span data-ttu-id="c83fb-104">たとえば、ユーザーがレポートの名前、データ ソース、その他のレポート サーバー アイテムを追加または更新できるアプリケーションで、ユーザーが入力するテキストを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c83fb-104">For example, in applications that enable users to add or update the name of a report, data source, or other report server item, you should validate the text that a user might enter.</span></span> <span data-ttu-id="c83fb-105">また、要求をレポート サーバーに送信する前に予約文字を常に確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c83fb-105">You should always check for reserved characters before sending the request to a report server.</span></span> <span data-ttu-id="c83fb-106">コードで条件付きの **if** ステートメントまたは他の論理構造を使って、要求をレポート サーバーに送信するために必要な条件を満たしていないことをユーザーに警告します。</span><span class="sxs-lookup"><span data-stu-id="c83fb-106">Use conditional **if** statements or other logical constructs in your code to alert the user that they have not met the conditions necessary to send requests to the report server.</span></span>  
  
 <span data-ttu-id="c83fb-107">次の単純な C# の例では、ユーザーがスラッシュ (/) 文字を含む名前でレポートを作成しようとすると、わかりやすいエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c83fb-107">In the following, simplified C# example, users are presented with a friendly error message when they attempt to create a report with a name that contains a forward slash (/) character.</span></span>  
  
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
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 <span data-ttu-id="c83fb-108">要求がレポート サーバーに送信される前に回避できるエラーの種類については、「[SoapException エラー テーブル](../soapexception-class/soapexception-errors-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c83fb-108">For more information about the types of errors that can be prevented before requests are sent to the report server, see [SoapException Errors Table](../soapexception-class/soapexception-errors-table.md).</span></span> <span data-ttu-id="c83fb-109">try ブロックまたは catch ブロックを使用して上記の例をさらに強化した内容については、「[Try ブロックと Catch ブロックの使用](using-try-and-catch-blocks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c83fb-109">For more information about further enhancing the previous example using try/catch blocks, see [Using Try and Catch Blocks](using-try-and-catch-blocks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83fb-110">参照</span><span class="sxs-lookup"><span data-stu-id="c83fb-110">See Also</span></span>  
 <span data-ttu-id="c83fb-111">[Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="c83fb-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="c83fb-112">Reporting Services SoapException クラス</span><span class="sxs-lookup"><span data-stu-id="c83fb-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
