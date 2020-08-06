---
title: PowerPivot からの復元 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dbb0e7867451e67eaa1503c54d7e3da1c276965
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738827"
---
# <a name="restore-from-powerpivot"></a><span data-ttu-id="94cce-102">PowerPivot から復元</span><span class="sxs-lookup"><span data-stu-id="94cce-102">Restore from PowerPivot</span></span>
  <span data-ttu-id="94cce-103">SQL Server Management Studio の PowerPivot から復元機能を使って、テーブル モードで実行されている Analysis Services インスタンス上に新しいテーブル モデル データベースを作成したり、PowerPivot ブック (.xlsx) から既存のデータベースに復元したりできます。</span><span class="sxs-lookup"><span data-stu-id="94cce-103">You can use the Restore from PowerPivot feature in SQL Server Management Studio to create a new Tabular model database on an Analysis Services instance (running in Tabular mode), or restore to an existing database from a PowerPivot workbook (.xlsx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94cce-104">SQL Server Data Tools の PowerPivot からのインポート プロジェクト テンプレートが同様の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="94cce-104">The Import from PowerPivot project template in SQL Server Data Tools provides similar functionality.</span></span> <span data-ttu-id="94cce-105">詳細については、「 [PowerPivot からのインポート &#40;SSAS 表形式&#41;](import-from-power-pivot-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94cce-105">For more information, see [Import from PowerPivot &#40;SSAS Tabular&#41;](import-from-power-pivot-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="94cce-106">PowerPivot から復元機能を使用する場合、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="94cce-106">When using Restore from PowerPivot, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="94cce-107">PowerPivot から復元機能を使用するには、サーバー管理者ロールのメンバーとして Analysis Services インスタンスにログオンしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="94cce-107">In order to use Restore from PowerPivot, you must be logged on as a member of the Server Administrators role on the Analysis Services instance.</span></span>  
  
-   <span data-ttu-id="94cce-108">Analysis Services インスタンス サービス アカウントには、復元するブック ファイルの読み取り権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="94cce-108">The Analysis Services instance service account must have Read permissions on the workbook file you are restoring from.</span></span>  
  
-   <span data-ttu-id="94cce-109">既定では、PowerPivot からデータベースを復元する場合は、テーブル モデル データベースのデータ ソースの権限借用情報プロパティは既定値に設定されており、Analysis Services インスタンス サービス アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="94cce-109">By default, when you restore a database from PowerPivot, the Tabular model database Data Source Impersonation Info property is set to Default, which specifies the Analysis Services instance service account.</span></span> <span data-ttu-id="94cce-110">権限借用の資格情報をデータベース プロパティの Windows ユーザー アカウントに変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="94cce-110">It is recommended you change the impersonation credentials to a Windows user account in Database Properties.</span></span> <span data-ttu-id="94cce-111">詳細については、「[権限借用 (SSAS テーブル)](impersonation-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94cce-111">For more information, see [Impersonation &#40;SSAS Tabular&#41;](impersonation-ssas-tabular.md).</span></span>  
  
-   <span data-ttu-id="94cce-112">PowerPivot データ モデルのデータは、Analysis Services インスタンス上の既存または新規のテーブル モデル データベースにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="94cce-112">Data in the PowerPivot data model will be copied into an existing or new Tabular model database on the Analysis Services instance.</span></span> <span data-ttu-id="94cce-113">PowerPivot ブックにリンク テーブルが含まれている場合は、新規テーブルを使用して作成されたテーブルのように、データ ソースを使用せずにテーブルとして再作成されます。</span><span class="sxs-lookup"><span data-stu-id="94cce-113">If your PowerPivot workbook contains linked tables, they will be recreated as a table without a data source, similar to a table created using Paste To New table.</span></span>  
  
### <a name="to-restore-from-powerpivot"></a><span data-ttu-id="94cce-114">PowerPivot から復元するには</span><span class="sxs-lookup"><span data-stu-id="94cce-114">To Restore from PowerPivot</span></span>  
  
1.  <span data-ttu-id="94cce-115">SSMS で、復元先の Active Directory インスタンスの [**データベース**] を右クリックし、[ **PowerPivot から復元**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94cce-115">In SSMS, in the Active Directory instance you want to restore to, right click **Databases**, and then click **Restore from PowerPivot**.</span></span>  
  
2.  <span data-ttu-id="94cce-116">[ **PowerPivot から復元**] ダイアログボックスの [**復元元**] の [**バックアップファイル**] で、[**参照**] をクリックし、復元元の abf または .xslx ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="94cce-116">In the **Restore from PowerPivot** dialog box, in **Restore Source**, in **Backup file**, click **Browse**, and then select an .abf or .xslx file to restore from.</span></span>  
  
3.  <span data-ttu-id="94cce-117">**[復元対象]** の **[データベースの復元]** で、新しいデータベースまたは既存のデータベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="94cce-117">In **Restore Target**, in **Restore database**, type a name for a new database or for an existing database.</span></span> <span data-ttu-id="94cce-118">名前を指定しない場合は、ブック名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="94cce-118">If you do not specify a name, the name of the workbook is used.</span></span>  
  
4.  <span data-ttu-id="94cce-119">**[ストレージの場所]** で、 **[参照]** をクリックし、データベースを格納する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="94cce-119">In **Storage location**, click **Browse**, and then select a location to store the database.</span></span>  
  
5.  <span data-ttu-id="94cce-120">**[オプション]** で、 **[セキュリティ情報を含める]** チェック ボックスをオンのままにします。</span><span class="sxs-lookup"><span data-stu-id="94cce-120">In **Options**, leave **Include security information** checked.</span></span> <span data-ttu-id="94cce-121">PowerPivot ブックから復元する場合は、この設定は適用されません。</span><span class="sxs-lookup"><span data-stu-id="94cce-121">When restoring from a PowerPivot workbook, this setting does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94cce-122">参照</span><span class="sxs-lookup"><span data-stu-id="94cce-122">See Also</span></span>  
 <span data-ttu-id="94cce-123">[SSAS 表形式&#41;&#40;テーブルモデルデータベース](tabular-model-databases-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="94cce-123">[Tabular Model Databases &#40;SSAS Tabular&#41;](tabular-model-databases-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="94cce-124">PowerPivot からのインポート &#40;SSAS 表形式&#41;</span><span class="sxs-lookup"><span data-stu-id="94cce-124">Import from PowerPivot &#40;SSAS Tabular&#41;</span></span>](import-from-power-pivot-ssas-tabular.md)  
  
  
