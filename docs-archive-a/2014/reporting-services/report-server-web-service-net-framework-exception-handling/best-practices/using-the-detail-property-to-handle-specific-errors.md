---
title: Detail プロパティを使用したエラー処理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f8ac62dc381d8f665a44fc0897ba1f4215aa8e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719538"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a><span data-ttu-id="cdefd-102">Detail プロパティを使用したエラー処理</span><span class="sxs-lookup"><span data-stu-id="cdefd-102">Using the Detail Property to Handle Specific Errors</span></span>
  <span data-ttu-id="cdefd-103">例外を細かく分類するために、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] によって、SOAP 例外の **Detail** プロパティの子要素の **InnerText** プロパティにある追加のエラー情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="cdefd-103">To further classify exceptions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] returns additional error information in the **InnerText** property of the child elements in the SOAP exception's **Detail** property.</span></span> <span data-ttu-id="cdefd-104">**Detail** プロパティは **XmlNode** オブジェクトであるため、次のコードを使って **Message** 子要素の内部テキストにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cdefd-104">Because the **Detail** property is an **XmlNode** object, you can access the inner text of the **Message** child element using the following code.</span></span>  
  
 <span data-ttu-id="cdefd-105">**Detail** プロパティに含まれる有効なすべての子要素の一覧については、「[Detail プロパティ](../soapexception-class/detail-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdefd-105">For a list of all of the available child elements contained in the **Detail** property, see [Detail Property](../soapexception-class/detail-property.md).</span></span> <span data-ttu-id="cdefd-106">詳細については、SDK ドキュメントの「詳細プロパティ」を参照してください [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cdefd-106">For more information, see "Detail Property" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 <span data-ttu-id="cdefd-107">次のコード行によって、SOAP 例外で返される特定のエラー コードがコンソールに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="cdefd-107">The following line of code writes the specific error code being returned in the SOAP Exception to the console.</span></span> <span data-ttu-id="cdefd-108">また、エラー コードを評価して特定のアクションを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="cdefd-108">You could also evaluate the error code and perform specific actions.</span></span>  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdefd-109">参照</span><span class="sxs-lookup"><span data-stu-id="cdefd-109">See Also</span></span>  
 <span data-ttu-id="cdefd-110">[Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="cdefd-110">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 <span data-ttu-id="cdefd-111">[Reporting Services SoapException クラス](../soapexception-class/reporting-services-soapexception-class.md) </span><span class="sxs-lookup"><span data-stu-id="cdefd-111">[Reporting Services SoapException Class](../soapexception-class/reporting-services-soapexception-class.md) </span></span>  
 [<span data-ttu-id="cdefd-112">SoapException エラー テーブル</span><span class="sxs-lookup"><span data-stu-id="cdefd-112">SoapException Errors Table</span></span>](../soapexception-class/soapexception-errors-table.md)  
  
  
