---
title: バックアップオプション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- databases [Analysis Services], backing up
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
author: minewiskan
ms.author: owend
ms.openlocfilehash: f9fc674e699a3078ebd39d50fde96d632ae20493
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632161"
---
# <a name="backup-options"></a><span data-ttu-id="c9f3b-102">バックアップ オプション</span><span class="sxs-lookup"><span data-stu-id="c9f3b-102">Backup Options</span></span>
  <span data-ttu-id="c9f3b-103">データベースをバックアップするにはさまざまな方法があり、すべての方法で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバー管理者とデータベース管理者のアクセス許可を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-103">There are many ways to back up your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases and they all require that you have server administrator and database administrator permissions.</span></span> <span data-ttu-id="c9f3b-104">**で** [バックアップ] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを開き、適切なオプション構成を選択し、ダイアログ ボックスから直接バックアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-104">You can open the **Backup** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the appropriate options configuration, and then run the backup from the dialog box itself.</span></span> <span data-ttu-id="c9f3b-105">または、ファイルに既に指定されている設定を使用してスクリプトを作成できます。このスクリプトを保存して、必要に応じて実行できます。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-105">Or, you can create a script using the settings already specified in the file; the script can then be saved and run as frequently as required.</span></span>  
  
## <a name="backup-and-synchronize"></a><span data-ttu-id="c9f3b-106">バックアップと同期</span><span class="sxs-lookup"><span data-stu-id="c9f3b-106">Backup and Synchronize</span></span>  
 <span data-ttu-id="c9f3b-107">データベースが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のリモート インスタンスに存在する場合は、同期機能を使用してデータベースをローカルのインスタンスにバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-107">If the database is located on a remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the synchronization feature to back up the database to the local instance.</span></span> <span data-ttu-id="c9f3b-108">データベースの開発ビルドは、この方法で運用環境に移行できます。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-108">Development builds of a database can be moved into production in this manner.</span></span> <span data-ttu-id="c9f3b-109">従来のファイル ベースのバックアップおよび復元機能を使用して、開発ビルドを運用環境に移行することもできますが、同期機能を使用すると、追加の機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-109">You can also use the conventional, file based, backup and restore to move the development build into production, but synchronization provides additional functionality.</span></span> <span data-ttu-id="c9f3b-110">同期機能を使用すると、たとえば、開発用コンピューターと実稼動コンピューターにそれぞれ異なるセキュリティ設定を使用できます。つまり、セキュリティ設定を管理し、ロール以外のすべてのオブジェクトを同期することができます。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-110">For example, you can have security settings which are different for the development and production computers; synchronization will provide you the option to maintain those settings and synchronize all objects other than roles.</span></span> <span data-ttu-id="c9f3b-111">また、コピー元コンピューターとコピー先コンピューターで異なるこれらのオブジェクトの増分更新も、通常、同期機能で行います。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-111">Also, synchronization typically does an incremental update of those objects which are different for the source and destination computers.</span></span> <span data-ttu-id="c9f3b-112">この種の増分バックアップは、バックアップおよび復元機能では利用できません。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-112">This kind of incremental backup is not available using the backup/restore feature.</span></span> <span data-ttu-id="c9f3b-113">詳細については、「 [Analysis Services データベースの同期](synchronize-analysis-services-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-113">For more information, see [Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c9f3b-114">Analysis Services サービス アカウントには、各ファイルに指定されたバックアップ場所に対する書き込み権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-114">The Analysis Services service account must have permission to write to the backup location specified for each file.</span></span> <span data-ttu-id="c9f3b-115">また、ユーザーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの管理者ロールを持っているか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9f3b-115">Also, the user must have one of the following roles: administrator role on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be backed up.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f3b-116">参照</span><span class="sxs-lookup"><span data-stu-id="c9f3b-116">See Also</span></span>  
 <span data-ttu-id="c9f3b-117">[[データベースのバックアップ] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c9f3b-117">[Backup Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c9f3b-118">[Analysis Services データベースのバックアップと復元](backup-and-restore-of-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="c9f3b-118">[Backup and Restore of Analysis Services Databases](backup-and-restore-of-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="c9f3b-119">[XMLA&#41;&#40;Backup 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="c9f3b-119">[Backup Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) </span></span>  
 [<span data-ttu-id="c9f3b-120">データベースのバックアップ、復元、および同期 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="c9f3b-120">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
