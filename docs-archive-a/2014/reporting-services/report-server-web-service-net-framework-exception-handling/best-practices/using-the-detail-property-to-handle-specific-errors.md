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
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Detail プロパティを使用したエラー処理
  例外を細かく分類するために、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] によって、SOAP 例外の **Detail** プロパティの子要素の **InnerText** プロパティにある追加のエラー情報が返されます。 **Detail** プロパティは **XmlNode** オブジェクトであるため、次のコードを使って **Message** 子要素の内部テキストにアクセスできます。  
  
 **Detail** プロパティに含まれる有効なすべての子要素の一覧については、「[Detail プロパティ](../soapexception-class/detail-property.md)」を参照してください。 詳細については、SDK ドキュメントの「詳細プロパティ」を参照してください [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。  
  
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
  
 次のコード行によって、SOAP 例外で返される特定のエラー コードがコンソールに書き込まれます。 また、エラー コードを評価して特定のアクションを実行することもできます。  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a>参照  
 [Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](../soapexception-class/reporting-services-soapexception-class.md)   
 [SoapException エラー テーブル](../soapexception-class/soapexception-errors-table.md)  
  
  
