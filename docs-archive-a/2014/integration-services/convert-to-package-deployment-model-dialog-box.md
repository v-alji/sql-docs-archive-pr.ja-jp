---
title: '[パッケージ配置モデルに変換] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.bids.converttolegacydeployment.f1
ms.assetid: 9e60a34a-10f7-48d1-966f-b3ff236ab4b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b52932ad26f8cebd2e67b0025f4b881241119f6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641802"
---
# <a name="convert-to-package-deployment-model-dialog-box"></a><span data-ttu-id="e446e-102">[パッケージ配置モデルに変換] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="e446e-102">Convert to Package Deployment Model Dialog Box</span></span>
  <span data-ttu-id="e446e-103">**[パッケージ配置モデルに変換]** コマンドを使用すると、パッケージをパッケージ配置モデルに変換できます。この変換は、プロジェクトおよびプロジェクト内の各パッケージとそのモデルとの互換性を確認した後に行います。</span><span class="sxs-lookup"><span data-stu-id="e446e-103">The **Convert to Package Deployment Model** command allows you to convert a package to the package deployment model after checking the project and each package in the project for compatibility with that model.</span></span> <span data-ttu-id="e446e-104">パラメーターなど、プロジェクト配置モデルに固有の機能をパッケージで使用する場合は、パッケージを変換できません。</span><span class="sxs-lookup"><span data-stu-id="e446e-104">If a package uses features unique to the project deployment model, such as parameters, then the package cannot be converted.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="e446e-105">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="e446e-105">Task List</span></span>  
 <span data-ttu-id="e446e-106">パッケージをパッケージ配置モデルに変換するには、2 つの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e446e-106">Converting a package to the package deployment model requires two steps.</span></span>  
  
1.  <span data-ttu-id="e446e-107">**[プロジェクト]** メニューの **[パッケージ配置モデルに変換]** をクリックすると、プロジェクトおよび各パッケージとこのモデルとの互換性が確認されます。</span><span class="sxs-lookup"><span data-stu-id="e446e-107">When you select the **Convert to Package Deployment Model** command from the **Project** menu, the project and each package are checked for compatibility with this model.</span></span> <span data-ttu-id="e446e-108">結果は **[結果]** テーブルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e446e-108">The results are displayed in the **Results** table.</span></span>  
  
     <span data-ttu-id="e446e-109">互換性テストに失敗したプロジェクトまたはパッケージがある場合は、 **[結果]** 列の **[失敗]** をクリックして詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="e446e-109">If the project or a package fails the compatibility test, click **Failed** in the **Result** column for more information.</span></span> <span data-ttu-id="e446e-110">この情報のコピーをテキスト ファイルに保存するには、 **[レポートの保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e446e-110">Click **Save Report** to save a copy of this information to a text file.</span></span>  
  
2.  <span data-ttu-id="e446e-111">プロジェクトとすべてのパッケージの互換性テストが成功した場合は、 **[OK]** をクリックしてパッケージを変換します。</span><span class="sxs-lookup"><span data-stu-id="e446e-111">If the project and all packages pass the compatibility test, then click **OK** to convert the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e446e-112">プロジェクトをプロジェクト配置モデルに変換するには、**Integration Services プロジェクト変換ウィザード**を使用します。</span><span class="sxs-lookup"><span data-stu-id="e446e-112">To convert a project to the project deployment model, use the **Integration Services Project Conversion Wizard**.</span></span> <span data-ttu-id="e446e-113">詳細については、「 [Integration Services プロジェクトの変換ウィザード](../../2014/integration-services/integration-services-project-conversion-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e446e-113">For more information, see [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e446e-114">参照</span><span class="sxs-lookup"><span data-stu-id="e446e-114">See Also</span></span>  
 <span data-ttu-id="e446e-115">[プロジェクトとパッケージの配置](packages/deploy-integration-services-ssis-projects-and-packages.md) </span><span class="sxs-lookup"><span data-stu-id="e446e-115">[Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md) </span></span>  
 <span data-ttu-id="e446e-116">[SSIS&#41;&#40;パッケージの配置](packages/legacy-package-deployment-ssis.md) </span><span class="sxs-lookup"><span data-stu-id="e446e-116">[Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md) </span></span>  
 [<span data-ttu-id="e446e-117">Integration Services プロジェクト変換ウィザード</span><span class="sxs-lookup"><span data-stu-id="e446e-117">Integration Services Project Conversion Wizard</span></span>](../../2014/integration-services/integration-services-project-conversion-wizard.md)  
  
  
