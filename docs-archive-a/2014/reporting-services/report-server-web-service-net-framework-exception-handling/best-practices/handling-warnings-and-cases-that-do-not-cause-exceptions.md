---
title: 例外が発生しない警告および状況の処理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], warnings that don't cause
- warnings [Reporting Services]
ms.assetid: 475c0713-6265-44e7-9ebc-ebdd1b89e0af
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 88d3daf63cf5f04975a2941d0634f357ce81456c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717379"
---
# <a name="handling-warnings-and-cases-that-do-not-cause-exceptions"></a><span data-ttu-id="4f70a-102">例外が発生しない警告および状況の処理</span><span class="sxs-lookup"><span data-stu-id="4f70a-102">Handling Warnings and Cases That Do Not Cause Exceptions</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="4f70a-103">では、警告および特定のエラーに対して例外をスローしません。</span><span class="sxs-lookup"><span data-stu-id="4f70a-103">does not throw exceptions for warnings and certain errors.</span></span> <span data-ttu-id="4f70a-104">たとえば、<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> メソッドを使用して新しいレポートをレポート サーバーにパブリッシュしたときに警告が発生した場合、その警告は <xref:ReportService2010.Warning> オブジェクトの配列として返されます。</span><span class="sxs-lookup"><span data-stu-id="4f70a-104">For example, when you use the <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> method to publish a new report to a report server, any warnings that occur are returned as an array of <xref:ReportService2010.Warning> objects.</span></span> <span data-ttu-id="4f70a-105">それらの警告は、適切な処置を実行できるように処理および表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f70a-105">These warnings should be handled and displayed so that appropriate action can be taken.</span></span>  
  
```vb  
Try  
   rs.CreateCatalogItem(name, parentFolder, False, definition, Nothing, warnings)  
  
   If Not (warnings.Length = 0) Then  
      Dim warning As Warning  
      For Each warning In warnings  
         Console.WriteLine(warning.Message)  
      Next warning  
   Else  
      Console.WriteLine("Report {0} created successfully with no warnings", name)  
   End If  
  
Catch ex As SoapException  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.CreateCatalogItem("Report", name, parentFolder, false, definition, null, out warnings);  
  
   if (warnings.Length != 0)  
   {  
      foreach (Warning warning in warnings)  
      {  
         Console.WriteLine(warning.Message);  
      }  
   }  
   else  
      Console.WriteLine("Report {0} created successfully with no warnings", name);  
}  
  
catch (SoapException ex)  
{  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
 <span data-ttu-id="4f70a-106">もう 1 つのエラー処理方法は、特定のメソッドの戻り値を評価することです。</span><span class="sxs-lookup"><span data-stu-id="4f70a-106">Another way to handle errors is to evaluate the return values of certain methods.</span></span> <span data-ttu-id="4f70a-107">たとえば、<xref:ReportService2010.ReportingService2010.FindItems%2A> メソッドを使用して、レポート サーバー データベースの特定のアイテムを検索できます。</span><span class="sxs-lookup"><span data-stu-id="4f70a-107">For example, the <xref:ReportService2010.ReportingService2010.FindItems%2A> method can be used to search for specific items in the report server database.</span></span> <span data-ttu-id="4f70a-108">検索条件に一致するアイテムが見つからない場合、<xref:ReportService2010.CatalogItem> オブジェクトの null 配列が返されます。</span><span class="sxs-lookup"><span data-stu-id="4f70a-108">If no items are found that match the search criteria, a null array of <xref:ReportService2010.CatalogItem> objects is returned.</span></span> <span data-ttu-id="4f70a-109">その配列を評価し、`null` を調べて、アイテムが見つからなかった場合はユーザーに知らせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f70a-109">You should evaluate the array, check for `null`, and let the user know if no items were found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f70a-110">参照</span><span class="sxs-lookup"><span data-stu-id="4f70a-110">See Also</span></span>  
 <xref:ReportService2010.CatalogItem>   
 <span data-ttu-id="4f70a-111">[Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="4f70a-111">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="4f70a-112">Reporting Services SoapException クラス</span><span class="sxs-lookup"><span data-stu-id="4f70a-112">Reporting Services SoapException Class</span></span>](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
