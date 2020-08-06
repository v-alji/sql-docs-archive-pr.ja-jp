---
title: パッケージをプログラムで保存 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2879c4213b2c9c0bf395c103de0d1bc37e4daab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634599"
---
# <a name="saving-a-package-programmatically"></a><span data-ttu-id="c1021-102">パッケージをプログラムで保存</span><span class="sxs-lookup"><span data-stu-id="c1021-102">Saving a Package Programmatically</span></span>
  <span data-ttu-id="c1021-103">プログラムにより新しいパッケージを構築したり、既存のパッケージを変更した後には、通常は変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="c1021-103">After building a new package programmatically, or modifying an existing one, you usually want to save your changes.</span></span>  
  
 <span data-ttu-id="c1021-104">このトピックでパッケージを保存するために使用するすべてのメソッドには、`Microsoft.SqlServer.ManagedDTS` アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="c1021-104">All of the methods used in this topic to save packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="c1021-105">新しいプロジェクトに参照を追加した後、 <xref:Microsoft.SqlServer.Dts.Runtime> またはステートメントを使用して名前空間をインポートし `using` `Imports` ます。</span><span class="sxs-lookup"><span data-stu-id="c1021-105">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
## <a name="saving-a-package-programmatically"></a><span data-ttu-id="c1021-106">パッケージをプログラムで保存</span><span class="sxs-lookup"><span data-stu-id="c1021-106">Saving a Package Programmatically</span></span>  
 <span data-ttu-id="c1021-107">プログラムによりパッケージを保存するには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスの次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c1021-107">To save a package programmatically, call one of the following methods of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> class:</span></span>  
  
|<span data-ttu-id="c1021-108">保存先</span><span class="sxs-lookup"><span data-stu-id="c1021-108">Storage Location</span></span>|<span data-ttu-id="c1021-109">呼び出すメソッド</span><span class="sxs-lookup"><span data-stu-id="c1021-109">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="c1021-110">ファイル</span><span class="sxs-lookup"><span data-stu-id="c1021-110">File</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|<span data-ttu-id="c1021-111">[SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="c1021-111">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> <span data-ttu-id="c1021-112">or</span><span class="sxs-lookup"><span data-stu-id="c1021-112">or</span></span><br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c1021-113">SSIS パッケージ ストアを操作するための <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスのメソッドは、"." またはローカル サーバーのサーバー名のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="c1021-113">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store only support "." or the server name for the local server.</span></span> <span data-ttu-id="c1021-114">"(local)" や "localhost" は使用できません。</span><span class="sxs-lookup"><span data-stu-id="c1021-114">You cannot use "(local)" or "localhost".</span></span>  
  
<span data-ttu-id="c1021-115">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="c1021-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c1021-116">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1021-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c1021-117">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="c1021-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c1021-118">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="c1021-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1021-119">参照</span><span class="sxs-lookup"><span data-stu-id="c1021-119">See Also</span></span>  
 [<span data-ttu-id="c1021-120">パッケージを保存する</span><span class="sxs-lookup"><span data-stu-id="c1021-120">Save Packages</span></span>](../save-packages.md)  
  
  
