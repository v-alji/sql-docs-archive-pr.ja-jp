---
title: Reporting Services スクリプト ファイルを書式設定する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], formats
- formats [Reporting Services], script files
ms.assetid: 85a207dd-4e0f-4d40-a41e-0c75f65d719c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c98a2f6561c3242fec34f7ca11c8304286ccebae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716038"
---
# <a name="format-a-reporting-services-script-file"></a><span data-ttu-id="a87ad-102">Reporting Services スクリプト ファイルを書式設定する</span><span class="sxs-lookup"><span data-stu-id="a87ad-102">Format a Reporting Services Script File</span></span>
  <span data-ttu-id="a87ad-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のスクリプトは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET コード ファイルであり、Web サービス記述言語 (WSDL) で構築されたプロキシに対して記述され、Reporting Services SOAP API を定義します。</span><span class="sxs-lookup"><span data-stu-id="a87ad-103">A [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] script is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET code file, written against a proxy that is built on Web Service Description Language (WSDL), which defines the Reporting Services SOAP API.</span></span> <span data-ttu-id="a87ad-104">スクリプト ファイルは、拡張子 .rss が付く Unicode または UTF-8 テキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="a87ad-104">A script file is stored as a Unicode or UTF-8 text file with the extension .rss.</span></span>  
  
 <span data-ttu-id="a87ad-105">スクリプト ファイルは [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] モジュールとして動作し、ユーザー定義プロシージャとモジュール レベル変数を含みます。</span><span class="sxs-lookup"><span data-stu-id="a87ad-105">The script file acts as a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] module and can contain user-defined procedures and module-level variables.</span></span> <span data-ttu-id="a87ad-106">スクリプト ファイルを正常に実行するには、スクリプト ファイルに Main プロシージャが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a87ad-106">For the script file to run successfully, it must contain a Main procedure.</span></span> <span data-ttu-id="a87ad-107">Main プロシージャは、スクリプト ファイルを実行したとき最初に呼び出されるプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="a87ad-107">The Main procedure is the first procedure that is accessed when your script file runs.</span></span> <span data-ttu-id="a87ad-108">Main で、Web サービスの操作を追加でき、ユーザー定義サブプロシージャを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a87ad-108">Main is where you can add your Web service operations and run your user defined subprocedures.</span></span> <span data-ttu-id="a87ad-109">次のコードによって Main プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="a87ad-109">The following code creates a Main procedure:</span></span>  
  
```  
Public Sub Main()  
    ' Your code goes here.  
End Sub  
```  
  
 <span data-ttu-id="a87ad-110">スクリプト環境は、レポート サーバーと自動的に接続し、Web プロキシ クラスを作成し、Web サービス プロキシ オブジェクトへの参照変数 (*rs*) を生成します。</span><span class="sxs-lookup"><span data-stu-id="a87ad-110">The script environment automatically connects to the report server, creates the Web proxy class, and generates a reference variable (*rs*) to the Web service proxy object.</span></span> <span data-ttu-id="a87ad-111">作成する個別のステートメントに必要なのは、Web サービス ライブラリで使用できる Web サービス操作を実行するために、 *rs* モジュール レベル変数を参照することだけです。</span><span class="sxs-lookup"><span data-stu-id="a87ad-111">Individual statements that you create need only refer to the *rs* module-level variable to perform any of the Web service operations that are available in the Web service library.</span></span> <span data-ttu-id="a87ad-112">次の [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] コードは、スクリプト ファイル内の Web サービス <xref:ReportService2010.ReportingService2010.ListChildren%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a87ad-112">The following [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] code calls the Web service <xref:ReportService2010.ReportingService2010.ListChildren%2A> method from within a script file:</span></span>  
  
```  
Public Sub Main()  
    Dim items() As CatalogItem  
    items = rs.ListChildren("/", True)  
  
    Dim item As CatalogItem  
    For Each item In items  
        Console.WriteLine(item.Name)  
    Next item  
End Sub   
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a87ad-113">ユーザーの資格情報はスクリプト環境によって管理され、RS.exe の使用によりコマンド プロンプト引数をとおして渡されます。</span><span class="sxs-lookup"><span data-stu-id="a87ad-113">User credentials are managed by the script environment and passed through command prompt arguments through the use of RS.exe.</span></span> <span data-ttu-id="a87ad-114">*rs* 変数を使用して Web サービスの認証を設定できますが、スクリプト環境を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a87ad-114">Although you can use the *rs* variable to set the authentication of the Web service, it is recommended that you use the script environment.</span></span> <span data-ttu-id="a87ad-115">スクリプト ファイル内自体では Web サービスを認証する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="a87ad-115">You do not need to authenticate the Web service in the script file itself.</span></span> <span data-ttu-id="a87ad-116">スクリプト環境の認証の詳細については、「 [RS.exe ユーティリティ &#40;SSRS&#41;](rs-exe-utility-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a87ad-116">For more information about authenticating the script environment, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span>  
  
 <span data-ttu-id="a87ad-117">スクリプト ファイル内では名前空間を宣言しません。</span><span class="sxs-lookup"><span data-stu-id="a87ad-117">You do not declare namespaces within the script file.</span></span> <span data-ttu-id="a87ad-118">スクリプト環境では、便利な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 名前空間、**System.Web.Services**、**System.Web.Services.Protocols**、**System.Xml**、**System.IO** が利用できます。</span><span class="sxs-lookup"><span data-stu-id="a87ad-118">The scripting environment makes several useful [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces available to you: **System.Web.Services**, **System.Web.Services.Protocols**, **System.Xml**, and **System.IO**.</span></span>  
  
 <span data-ttu-id="a87ad-119">スクリプトのサンプルについては、「 [SQL Server Reporting Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=177889)」参照してください。</span><span class="sxs-lookup"><span data-stu-id="a87ad-119">For script samples, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87ad-120">参照</span><span class="sxs-lookup"><span data-stu-id="a87ad-120">See Also</span></span>  
 <span data-ttu-id="a87ad-121">[レポート サーバー Web サービス](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="a87ad-121">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="a87ad-122">[テクニカル リファレンス (SSRS)](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a87ad-122">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="a87ad-123">RS.exe ユーティリティ &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a87ad-123">RS.exe Utility &#40;SSRS&#41;</span></span>](rs-exe-utility-ssrs.md)  
  
  
