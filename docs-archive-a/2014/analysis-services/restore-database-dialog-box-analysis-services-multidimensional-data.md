---
title: '[データベースの復元] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Restore.f1
ms.assetid: a3990d47-55e2-424e-8eac-87edc937e806
author: minewiskan
ms.author: owend
ms.openlocfilehash: f45a41eb10e81e1cfe1100045cc4d00353cb11fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743526"
---
# <a name="restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="b99d7-102">[データベースの復元] ダイアログ ボックス (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="b99d7-102">Restore Database Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b99d7-103">**の** [データベースの復元] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] バックアップ ファイル (.abf) 形式を使用するバックアップ ファイルから [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを復元できます。</span><span class="sxs-lookup"><span data-stu-id="b99d7-103">Use the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database from a backup file using the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Backup File (.abf) format.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b99d7-104">バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b99d7-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="b99d7-105">サーバーにインストールされていない [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。</span><span class="sxs-lookup"><span data-stu-id="b99d7-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="b99d7-106">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="b99d7-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b99d7-107">既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b99d7-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="b99d7-108">バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="b99d7-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="b99d7-109">**[データベースの復元] ダイアログ ボックスを表示するには**</span><span class="sxs-lookup"><span data-stu-id="b99d7-109">**To display the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="b99d7-110">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の **オブジェクト エクスプローラー** で、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの **[データベース]** フォルダー、またはデータベースを右クリックし、 **[復元]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b99d7-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, and then click **Restore**.</span></span>  
  
 <span data-ttu-id="b99d7-111">**[データベースの復元]** ダイアログ ボックスには、次のページがあります。</span><span class="sxs-lookup"><span data-stu-id="b99d7-111">The **Restore Database** dialog box contains the following pages.</span></span>  
  
## <a name="pages"></a><span data-ttu-id="b99d7-112">ページ</span><span class="sxs-lookup"><span data-stu-id="b99d7-112">Pages</span></span>  
 <span data-ttu-id="b99d7-113">**全般**</span><span class="sxs-lookup"><span data-stu-id="b99d7-113">**General**</span></span>  
 <span data-ttu-id="b99d7-114">このページを使用して、復元するデータベース、データベースの復元元となるバックアップ ファイル、およびデータベースの復元時に使用する全般オプションとパスワードを選択します。</span><span class="sxs-lookup"><span data-stu-id="b99d7-114">Use this page to select the database to restore, the backup file from which to restore the database, as well as the general options and password to use while restoring the database.</span></span> <span data-ttu-id="b99d7-115">このページの詳細については、「[[全般] &#40;[データベースの復元] ダイアログ ボックス&#41; &#40;Analysis Services - 多次元データ&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b99d7-115">For more information about this page, see [General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="b99d7-116">**パーティション**</span><span class="sxs-lookup"><span data-stu-id="b99d7-116">**Partitions**</span></span>  
 <span data-ttu-id="b99d7-117">このページを使用して、ローカル パーティションを指定された場所へ復元したり、リモート パーティションをリモート バックアップ ファイルから復元したりします。</span><span class="sxs-lookup"><span data-stu-id="b99d7-117">Use this page to restore local partitions to specified locations, and to restore remote partitions from remote backup files.</span></span> <span data-ttu-id="b99d7-118">このページの詳細については、「[[パーティション] &#40;[データベースの復元] ダイアログ ボックス&#41; &#40;Analysis Services - 多次元データ&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b99d7-118">For more information about this page, see [Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99d7-119">参照</span><span class="sxs-lookup"><span data-stu-id="b99d7-119">See Also</span></span>  
 <span data-ttu-id="b99d7-120">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b99d7-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="b99d7-121">Analysis Services データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="b99d7-121">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
