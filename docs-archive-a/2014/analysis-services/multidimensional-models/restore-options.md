---
title: 復元オプション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], restoring
- restoring databases [Analysis Services]
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3fa8da816e656521fb04ae7beb1127786e04e178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743553"
---
# <a name="restore-options"></a><span data-ttu-id="3f14c-102">[復元オプション]</span><span class="sxs-lookup"><span data-stu-id="3f14c-102">Restore Options</span></span>
  <span data-ttu-id="3f14c-103">データベースを復元する方法は多数ありますが、その場合は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーコンピューターとデータベースの両方に対する管理者権限が必要です [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3f14c-103">There are many ways to restore your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, all of which require that you have administrator permissions for both the server computer and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="3f14c-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元するには、 **で** [データベースの復元] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを開き、このダイアログ ボックスから適切なオプション構成を選択して、復元を実行します。</span><span class="sxs-lookup"><span data-stu-id="3f14c-104">To restore an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, you can open the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the appropriate options configuration and then run the restore from the dialog box.</span></span> <span data-ttu-id="3f14c-105">または、ファイルに既に指定されている設定を使用してスクリプトを作成できます。このスクリプトを保存して、必要に応じて実行できます。</span><span class="sxs-lookup"><span data-stu-id="3f14c-105">Or, you can create a script using the settings already specified in the file; the script can then be saved and run as often as needed.</span></span> <span data-ttu-id="3f14c-106">この場合、次のセクションの説明に従って、XMLA を使用して復元を実行します。</span><span class="sxs-lookup"><span data-stu-id="3f14c-106">In this way, the restore is completed by using XMLA, as described in the next section.</span></span>  
  
## <a name="restoring-databases-using-xmla"></a><span data-ttu-id="3f14c-107">XMLA を使用したデータベースの復元</span><span class="sxs-lookup"><span data-stu-id="3f14c-107">Restoring Databases Using XMLA</span></span>  
 <span data-ttu-id="3f14c-108">XMLA の Restore コマンドを使用すると、.abf ファイルに基づいて復元を実行することによって復元プロセスを自動化できます。</span><span class="sxs-lookup"><span data-stu-id="3f14c-108">The XMLA Restore command is a way to automate the restore process by running a restore based on an .abf file.</span></span> <span data-ttu-id="3f14c-109">Restore コマンドには数多くのプロパティがあり、セキュリティの定義、リモート パーティションの保存場所、リレーショナル OLAP (ROLAP) オブジェクトの再配置などを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3f14c-109">The Restore command has a number of properties that can be set to specify security definitions, where remote partitions should be stored, and the relocation of relational OLAP (ROLAP) objects.</span></span> <span data-ttu-id="3f14c-110">詳細については、「 [Restore 要素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f14c-110">For more information, see [Restore Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3f14c-111">バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f14c-111">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="3f14c-112">サーバーにインストールされていない [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。</span><span class="sxs-lookup"><span data-stu-id="3f14c-112">To restore an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="3f14c-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f14c-113">To overwrite an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f14c-114">既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3f14c-114">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="3f14c-115">バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="3f14c-115">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f14c-116">参照</span><span class="sxs-lookup"><span data-stu-id="3f14c-116">See Also</span></span>  
 <span data-ttu-id="3f14c-117">[[データベースの復元] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3f14c-117">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="3f14c-118">[Analysis Services データベースのバックアップと復元](backup-and-restore-of-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="3f14c-118">[Backup and Restore of Analysis Services Databases](backup-and-restore-of-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="3f14c-119">[XMLA&#41;&#40;Restore 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="3f14c-119">[Restore Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) </span></span>  
 [<span data-ttu-id="3f14c-120">データベースのバックアップ、復元、および同期 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="3f14c-120">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
