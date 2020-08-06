---
title: GetProperties メソッドのアイテム名前空間の設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- item properties [Reporting Services]
- ItemNamespaceHeader SOAP header
- GetProperties method
ms.assetid: b0a08639-3101-40a2-abe2-3a41753826d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 14e8147a9a7639dd357077b5d881e2d4ed87fcc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717378"
---
# <a name="setting-the-item-namespace-for-the-getproperties-method"></a><span data-ttu-id="90c37-102">GetProperties メソッドのアイテム名前空間の設定</span><span class="sxs-lookup"><span data-stu-id="90c37-102">Setting the Item Namespace for the GetProperties Method</span></span>
  <span data-ttu-id="90c37-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で <xref:ReportService2010.ItemNamespaceHeader> SOAP ヘッダーを使用すると、アイテムの完全なパスとアイテムの ID という 2 つの異なる識別子に基づいてアイテムのプロパティを取得できます。</span><span class="sxs-lookup"><span data-stu-id="90c37-103">You can use the <xref:ReportService2010.ItemNamespaceHeader> SOAP header in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to retrieve item properties based on two different item identifiers: the full path of the item or the ID of the item.</span></span>  
  
 <span data-ttu-id="90c37-104"><xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドへの呼び出しを作成する場合、一般的にはプロパティを取得するアイテムの完全なパスを引数として渡します。</span><span class="sxs-lookup"><span data-stu-id="90c37-104">When you make a call to the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method, you normally pass as an argument the full path of the item for which you want to retrieve properties.</span></span> <span data-ttu-id="90c37-105"><xref:ReportService2010.ItemNamespaceHeader> を使用すると、メソッド呼び出しの SOAP ヘッダーを設定して、アイテムの ID を識別子として渡すことによって <xref:ReportService2010.ReportingService2010.GetProperties%2A> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="90c37-105">By using <xref:ReportService2010.ItemNamespaceHeader>, you can set the SOAP header for your method call to enable you to use <xref:ReportService2010.ReportingService2010.GetProperties%2A> by passing the ID of the item as an identifier.</span></span>  
  
 <span data-ttu-id="90c37-106">次のコード サンプルは、アイテムの ID に基づいてアイテムのプロパティ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="90c37-106">The following code sample retrieves the values for item properties based on the ID of the item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90c37-107">既定では、<xref:ReportService2010.ItemNamespaceHeader> メソッドに完全なパス名をアイテム識別子として渡す場合は、<xref:ReportService2010.ReportingService2010.GetProperties%2A> の値を設定する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="90c37-107">By default, you do not need to set a value for the <xref:ReportService2010.ItemNamespaceHeader> if you pass to the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method the full path name as the item identifier.</span></span>  
  
```vb  
Imports System  
Imports System.Collections  
  
Class Sample  
   Sub Main()  
      Dim rs As New ReportingService2010()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      rs.Url = "http://<Server Name>/reportserver/ReportService2010.asmx"  
  
      Dim items() As CatalogItem  
  
      Try  
         ' Need the ID property of items. Normally, you would already have   
         ' this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", False)  
  
         ' Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = New ItemNamespaceHeader()  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased  
  
         ' Call GetProperties with item ID.  
         If Not (items Is Nothing) Then  
            Dim item As CatalogItem  
            For Each item In  items  
               Dim properties As [Property]() = rs.GetProperties(item.ID, Nothing)  
               Dim property As [Property]  
               For Each property In  properties  
                  Console.WriteLine(([property].Name + ": " + [property].Value))  
               Next property  
               Console.WriteLine()  
            Next item  
         End If  
  
      Catch e As Exception  
         Console.WriteLine((e.Message + ": " + e.StackTrace))  
      End Try  
   End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.Collections;  
  
class Sample  
{  
   static void Main()  
   {  
   ReportingService2010 rs = new ReportingService2010();  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      rs.Url = "http://<Server Name>/reportserver/ReportService2010.asmx";  
  
      CatalogItem[] items;  
  
      try  
      {  
         // Need the ID property of items. Normally, you would already have   
         // this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", false);  
  
         // Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = new ItemNamespaceHeader();  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased;  
  
         // Call GetProperties with item ID.  
         if (items != null)  
         {  
            foreach( CatalogItem item in items)  
            {  
               Property[] properties = rs.GetProperties(item.ID, null);  
               foreach (Property property in properties)  
               {  
                  Console.WriteLine(property.Name + ": " + property.Value);  
               }  
               Console.WriteLine();  
            }  
         }  
      }  
  
      catch (Exception e)  
      {  
         Console.WriteLine(e.Message);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="90c37-108">参照</span><span class="sxs-lookup"><span data-stu-id="90c37-108">See Also</span></span>  
 <span data-ttu-id="90c37-109">[SSRS&#41;&#40;テクニカルリファレンス](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="90c37-109">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="90c37-110">Reporting Services の SOAP ヘッダーの使用</span><span class="sxs-lookup"><span data-stu-id="90c37-110">Using Reporting Services SOAP Headers</span></span>](using-reporting-services-soap-headers.md)  
  
  
