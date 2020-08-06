---
title: ソース管理接続の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 077a09cdca0c0aff777184f04467ca39592690aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642331"
---
# <a name="change-source-control-connections"></a><span data-ttu-id="18145-102">ソース管理接続の変更</span><span class="sxs-lookup"><span data-stu-id="18145-102">Change Source Control Connections</span></span>
  <span data-ttu-id="18145-103">ソース管理のソリューションを初めて追加したり開いたりしたときには、ソース管理プロバイダーによって、ローカル ソリューション ディレクトリのルート フォルダーとそれに対応するサーバー フォルダーの関連付けが作成されます。</span><span class="sxs-lookup"><span data-stu-id="18145-103">The first time you add or open a solution from source control, your source control provider creates an association between the root folder of the local solution directory and its corresponding server folder.</span></span>  
  
 <span data-ttu-id="18145-104">ルート フォルダー (統合ルートとも呼ばれます) は、クライアントにあります。</span><span class="sxs-lookup"><span data-stu-id="18145-104">The root folder (also called unified root) resides on the client.</span></span> <span data-ttu-id="18145-105">これは、ソリューションやプロジェクトによって参照されるすべてのファイルを下位に含むフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="18145-105">It is the folder beneath which all the files referenced by a solution or project can be found.</span></span> <span data-ttu-id="18145-106">ソリューションの最新バージョン、バージョン履歴、およびステータス情報を確認するには、ソース管理サーバーにあるサーバー フォルダーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="18145-106">To find the latest version of a solution, its history, and its status information, locate the server folder, which resides on the source control server.</span></span> <span data-ttu-id="18145-107">サーバー フォルダーは、[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe ではプロジェクトと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="18145-107">In [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, server folders are called projects.</span></span>  
  
 <span data-ttu-id="18145-108">さまざまな状況で、ソリューションをサーバー フォルダーから切断してバインドを解除する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="18145-108">In many situations, you need to unbind or disconnect a solution from its server folder.</span></span> <span data-ttu-id="18145-109">たとえば、ソース管理プロバイダーが格納されているコンピューターが使用できない場合は、バックアップ コンピューターに接続してバックアップ サーバー フォルダーにソリューションを再バインドすると、作業を正常に再開できます。</span><span class="sxs-lookup"><span data-stu-id="18145-109">For example, if the computer on which your source control provider resides is unavailable, you can connect to a backup computer, rebind your solution to a backed-up server folder, and resume working normally.</span></span> <span data-ttu-id="18145-110">また、ソース管理プロジェクトが分割されている場合は、ソリューションを新しいプロジェクト バージョンがあるサーバー フォルダーへバインドする必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="18145-110">Also, if a source control project is forked, you may have to bind your solution to the server folder where the new project version resides.</span></span>  
  
 <span data-ttu-id="18145-111">ソリューションがバインドされているサーバー フォルダーを変更するには、ソース管理プロバイダーのユーザー インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="18145-111">Use the user interface of the source control provider to change the server folder that a solution is bound to.</span></span> <span data-ttu-id="18145-112">ソース管理ユーザー インターフェイスは、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境から開くことができます。</span><span class="sxs-lookup"><span data-stu-id="18145-112">You can open the source control user interface from within the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment.</span></span>  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a><span data-ttu-id="18145-113">Studio 環境からソース管理ユーザー インターフェイスを開くには</span><span class="sxs-lookup"><span data-stu-id="18145-113">To open the source control user interface from the Studio environment</span></span>  
  
1.  <span data-ttu-id="18145-114">[**ファイル**] メニューの [**ソース管理**] をポイントし、[ **Microsoft Visual SourceSafe の起動**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18145-114">On the **File** menu, point to **Source Control**, and then click **Launch Microsoft Visual SourceSafe**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18145-115">参照</span><span class="sxs-lookup"><span data-stu-id="18145-115">See Also</span></span>  
 <span data-ttu-id="18145-116">[ソース管理の基礎](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="18145-116">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="18145-117">[ソース管理オプションの設定](../../2014/database-engine/set-source-control-options.md) </span><span class="sxs-lookup"><span data-stu-id="18145-117">[Set Source Control Options](../../2014/database-engine/set-source-control-options.md) </span></span>  
 [<span data-ttu-id="18145-118">ソース管理からのファイルの除外</span><span class="sxs-lookup"><span data-stu-id="18145-118">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
