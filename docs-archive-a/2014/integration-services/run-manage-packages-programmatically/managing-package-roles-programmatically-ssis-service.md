---
title: プログラムによるパッケージのロールの管理 (SSIS Service) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dff54f3f90d9e008ae21c83c2a8fdc3f7440a5c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740135"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a><span data-ttu-id="b32f4-102">プログラムによるパッケージのロールの管理 (SSIS Service)</span><span class="sxs-lookup"><span data-stu-id="b32f4-102">Managing Package Roles Programmatically (SSIS Service)</span></span>
  <span data-ttu-id="b32f4-103">プログラムによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を操作する際に、どのロールをパッケージに適用できるかどうかを確認したり、個々のパッケージに適用されているロールを確認または設定することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="b32f4-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine which roles are available to apply to packages, or to determine or set the roles applied to an individual package.</span></span> <span data-ttu-id="b32f4-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすさまざまなメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b32f4-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides a variety of methods to satisfy these requirements.</span></span>

 <span data-ttu-id="b32f4-105">ロールは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** データベースに格納されたパッケージにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="b32f4-105">Roles apply only to packages stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** database.</span></span> <span data-ttu-id="b32f4-106">パッケージ ロールの詳細については、「[Integration Services のロール &#40;SSIS サービス&#41;](../security/integration-services-roles-ssis-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b32f4-106">For more information about package roles, see [Integration Services Roles &#40;SSIS Service&#41;](../security/integration-services-roles-ssis-service.md).</span></span>

 <span data-ttu-id="b32f4-107">このトピックで説明するすべてのメソッドには、`Microsoft.SqlServer.ManagedDTS` アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="b32f4-107">All the methods discussed in this topic require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="b32f4-108">新しいプロジェクトに参照を追加した後、 <xref:Microsoft.SqlServer.Dts.Runtime> またはステートメントを使用して名前空間をインポートし `using` `Imports` ます。</span><span class="sxs-lookup"><span data-stu-id="b32f4-108">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace by using a `using` or `Imports` statement.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="b32f4-109">SSIS パッケージ ストアを操作するための <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスのメソッドでは、"."、localhost、またはローカル サーバーのサーバー名のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b32f4-109">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="b32f4-110">"(local)" は使用できません。</span><span class="sxs-lookup"><span data-stu-id="b32f4-110">You cannot use "(local)".</span></span>

## <a name="determining-which-roles-are-available"></a><span data-ttu-id="b32f4-111">使用できるロールの確認</span><span class="sxs-lookup"><span data-stu-id="b32f4-111">Determining Which Roles Are Available</span></span>
 <span data-ttu-id="b32f4-112">特定のサーバーに格納されているパッケージで使用できるロールを確認するには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> クラスの <xref:Microsoft.SqlServer.Dts.Runtime.Application> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b32f4-112">To determine which roles are available for the packages stored on a particular server, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class.</span></span>

## <a name="determining-which-roles-are-assigned"></a><span data-ttu-id="b32f4-113">割り当てられたロールの確認</span><span class="sxs-lookup"><span data-stu-id="b32f4-113">Determining Which Roles Are Assigned</span></span>
 <span data-ttu-id="b32f4-114">特定のパッケージに既に割り当てられているロールを確認するには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b32f4-114">To determine which roles have already been assigned to a particular package, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> method.</span></span> <span data-ttu-id="b32f4-115">パッケージにロールを割り当てるには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b32f4-115">To assign roles to a package, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> method.</span></span>

<span data-ttu-id="b32f4-116">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="b32f4-116">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b32f4-117">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b32f4-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b32f4-118">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="b32f4-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b32f4-119">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="b32f4-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b32f4-120">参照</span><span class="sxs-lookup"><span data-stu-id="b32f4-120">See Also</span></span>
 [<span data-ttu-id="b32f4-121">Integration Services のロール (SSIS サービス)</span><span class="sxs-lookup"><span data-stu-id="b32f4-121">Integration Services Roles &#40;SSIS Service&#41;</span></span>](../security/integration-services-roles-ssis-service.md)


