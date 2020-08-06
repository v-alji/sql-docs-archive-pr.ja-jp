---
title: 配信拡張機能ライブラリの作成 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 63b32f93-4bab-4b07-bd72-39a47aca1cda
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c9891c2b0c1bb9c7d495b3ab1f8f2267ce04b79f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741570"
---
# <a name="creating-a-delivery-extension-library"></a><span data-ttu-id="8718a-102">配信拡張機能ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="8718a-102">Creating a Delivery Extension Library</span></span>
  <span data-ttu-id="8718a-103">作成する [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能は、それぞれ一意の名前空間に割り当てられ、ライブラリまたはアセンブリ ファイルに組み込まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8718a-103">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension you create should be assigned to a unique namespace and built into a library or assembly file.</span></span> <span data-ttu-id="8718a-104">名前空間の正確な名前はあまり重要ではありませんが、名前は他の拡張機能とは共有しない一意のものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8718a-104">The exact name of the namespace is not important, but it must be unique and not shared with any other extension.</span></span> <span data-ttu-id="8718a-105">会社の配信拡張機能には、独自に一意の名前空間を作成してください。</span><span class="sxs-lookup"><span data-stu-id="8718a-105">You should create your own unique namespaces for your company's delivery extensions.</span></span>  
  
 <span data-ttu-id="8718a-106">次の例は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を開始するためのコードを示しています。配信インターフェイスとユーティリティ クラスを含む名前空間を使用しています。</span><span class="sxs-lookup"><span data-stu-id="8718a-106">The following example shows the code to begin a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, which uses the namespaces that contain the delivery interfaces and any utility classes.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 <span data-ttu-id="8718a-107">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能をコンパイルする場合は、コンパイラに対して Microsoft.ReportingServices.Interfaces.dll への参照を指定する必要があります。配信拡張機能のインターフェイスとクラスがそこに格納されているためです。</span><span class="sxs-lookup"><span data-stu-id="8718a-107">When compiling a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, you must supply to the compiler a reference to Microsoft.ReportingServices.Interfaces.dll, because the delivery extension interfaces and classes are contained there.</span></span> <span data-ttu-id="8718a-108"><xref:Microsoft.ReportingServices.Interfaces> 名前空間は、<xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイス、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> インターフェイスなどを実装するために必要です。</span><span class="sxs-lookup"><span data-stu-id="8718a-108">The <xref:Microsoft.ReportingServices.Interfaces> namespace is needed to implement the <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface, the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface, and more.</span></span> <span data-ttu-id="8718a-109">たとえば、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を実装するために C# で書き込まれたコードを含むすべてのファイルが、拡張子 .cs が付いた 1 つのディレクトリに格納されている場合は、CompanyName.ExtensionName.dll に格納されたファイルをコンパイルするために、そのディレクトリから次のコマンドが発行されます。</span><span class="sxs-lookup"><span data-stu-id="8718a-109">For example, if all the files containing the code to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension written in C# were in a single directory with the extension .cs, the following command would be issued from that directory to compile the files stored in CompanyName.ExtensionName.dll.</span></span>  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 <span data-ttu-id="8718a-110">次のコード例は、拡張子 .vb が付く [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ファイルに使用されるコマンドを示しています。</span><span class="sxs-lookup"><span data-stu-id="8718a-110">The following code example shows the command that would be used for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] files with the extension .vb.</span></span>  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  <span data-ttu-id="8718a-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用して、配信拡張機能を設計、開発、および構築することもできます。</span><span class="sxs-lookup"><span data-stu-id="8718a-111">You can also design, develop, and build your delivery extension using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="8718a-112">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でのアセンブリ開発の詳細については、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8718a-112">For more information about developing assemblies in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8718a-113">参照</span><span class="sxs-lookup"><span data-stu-id="8718a-113">See Also</span></span>  
 <span data-ttu-id="8718a-114">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="8718a-114">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="8718a-115">[配信拡張機能の実装](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="8718a-115">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="8718a-116">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8718a-116">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
