---
title: データ処理拡張機能ライブラリの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 82f4b71b-dd39-467d-8d8c-6771eb2b12de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3c14ed699e94c7d8ed0f6f3d727e9ba6e355b7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743030"
---
# <a name="creating-a-data-processing-extension-library"></a><span data-ttu-id="3265f-102">データ処理拡張機能ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="3265f-102">Creating a Data Processing Extension Library</span></span>
  <span data-ttu-id="3265f-103">作成する各 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能は、一意の名前空間に割り当てられ、ライブラリまたはアセンブリ ファイルに組み込まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3265f-103">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension you create should be assigned to a unique namespace and built into a library or assembly file.</span></span> <span data-ttu-id="3265f-104">名前空間の正確な名前はあまり重要ではありませんが、名前は他の拡張機能とは共有しない一意のものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="3265f-104">The exact name of the namespace is not important, but it must be unique and not shared with any other extension.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="3265f-105">では、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] と共に出荷されるデータ処理拡張機能に名前空間 <xref:Microsoft.ReportingServices.DataProcessing> を使用しています。</span><span class="sxs-lookup"><span data-stu-id="3265f-105">uses the namespace <xref:Microsoft.ReportingServices.DataProcessing> for the data processing extensions that ship with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="3265f-106">独自のデータ処理拡張機能を使用する場合は、重複しない一意な名前空間を作成してください。</span><span class="sxs-lookup"><span data-stu-id="3265f-106">You should create your own unique namespaces for your company's data processing extensions.</span></span>  
  
 <span data-ttu-id="3265f-107">次の例は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能を開始するためのコードを示しています。データ処理インターフェイスとユーティリティ クラスを含む名前空間を使用しています。</span><span class="sxs-lookup"><span data-stu-id="3265f-107">The following example shows the code to begin a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, which uses the namespaces that contain the data processing interfaces and any utility classes.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.DataProcessing  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.DataProcessing;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 <span data-ttu-id="3265f-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能をコンパイルする場合は、コンパイラに対して Microsoft.ReportingServices.Interfaces.dll への参照を指定する必要があります。データ処理拡張機能のインターフェイスがそこに格納されているためです。</span><span class="sxs-lookup"><span data-stu-id="3265f-108">When compiling a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, you must supply to the compiler a reference to Microsoft.ReportingServices.Interfaces.dll, because the data processing extension interfaces are contained there.</span></span> <span data-ttu-id="3265f-109"><xref:Microsoft.ReportingServices.DataProcessing> 名前空間は、データ処理拡張機能インターフェイスを実装するために必要です。<xref:Microsoft.ReportingServices.Interfaces> 名前空間は、<xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスを実装するために必要です。</span><span class="sxs-lookup"><span data-stu-id="3265f-109">The <xref:Microsoft.ReportingServices.DataProcessing> namespace is needed to implement the data processing extension interfaces, and the <xref:Microsoft.ReportingServices.Interfaces> namespace is needed to implement the <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface.</span></span> <span data-ttu-id="3265f-110">たとえば、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] データ処理拡張機能を実装するための C# コードを含むすべてのファイルが、拡張子が .cs である 1 つのディレクトリに格納されている場合、CompanyName.ExtensionName.dll に格納されたファイルをコンパイルするために、そのディレクトリから次のコマンドが発行されます。</span><span class="sxs-lookup"><span data-stu-id="3265f-110">For example, if all the files containing the code to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension written in C# were in a single directory with the extension .cs, the following command would be issued from that directory to compile the files stored in CompanyName.ExtensionName.dll.</span></span>  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 <span data-ttu-id="3265f-111">次のコード例は、拡張子 .vb が付く [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ファイルに使用されるコマンドを示しています。</span><span class="sxs-lookup"><span data-stu-id="3265f-111">The following code example shows the command that would be used for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] files with the extension .vb.</span></span>  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3265f-112">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用して、データ処理拡張機能を設計、開発、および構築することもできます。</span><span class="sxs-lookup"><span data-stu-id="3265f-112">You can also design, develop, and build your data processing extension using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="3265f-113">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でのアセンブリ開発の詳細については、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3265f-113">For more information about developing assemblies in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3265f-114">参照</span><span class="sxs-lookup"><span data-stu-id="3265f-114">See Also</span></span>  
 <span data-ttu-id="3265f-115">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="3265f-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="3265f-116">[データ処理拡張機能の実装](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3265f-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="3265f-117">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="3265f-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
