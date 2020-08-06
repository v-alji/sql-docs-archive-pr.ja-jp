---
title: SSIS ツールボックス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.toolboxcommon.F1
- sql12.dts.designer.toolbox.F1
- sql12.dts.designer.toolboxfavorites.F1
ms.assetid: 552ff592-eeef-46e8-b4a2-9b2384c869aa
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed35218c84c77d3116ab8c897fe51fab5d6359aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718507"
---
# <a name="ssis-toolbox"></a><span data-ttu-id="b6b01-102">SSIS ツールボックス</span><span class="sxs-lookup"><span data-stu-id="b6b01-102">SSIS Toolbox</span></span>
  <span data-ttu-id="b6b01-103">新しい **SSIS ツールボックス**には、ローカル コンピューターにインストールされているすべてのコンポーネント (SQL Server 2008 および 2008 R2 用に作成されたサードパーティのコンポーネントを含みます) が自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-103">All components that are installed on the local machine, including third-party components built for SQL Server 2008 and 2008 R2, now automatically appear in the new **SSIS Toolbox**.</span></span> <span data-ttu-id="b6b01-104">他のコンポーネントをインストールするときは、ツールボックスの内側を右クリックし、 **[ツールボックスの更新]** をクリックして、コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6b01-104">When you install additional components, right-click inside the toolbox and then click **Refresh Toolbox** to add the components.</span></span>  
  
 <span data-ttu-id="b6b01-105">ツールボックスからコンポーネントについての詳細情報に簡単にアクセスできます。コンポーネントをクリックすると、ツールボックスの下部に説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-105">You can easily access more information about a component from the toolbox, by clicking the component to view a description at the bottom of the toolbox.</span></span> <span data-ttu-id="b6b01-106">説明の横にある [ヘルプ] ボタンをクリックすると、オンライン ブックのトピックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-106">Click the Help button next to the description to display the Books Online topic.</span></span> <span data-ttu-id="b6b01-107">特定のコンポーネントでは、コンポーネントを構成および使用する方法を示すサンプルにアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-107">For certain components, you can also access samples that demonstrate how to configure and use the components.</span></span> <span data-ttu-id="b6b01-108">サンプルは、 [MSDN](https://go.microsoft.com/fwlink/?LinkId=259189)から利用できます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-108">The samples are available on [MSDN](https://go.microsoft.com/fwlink/?LinkId=259189).</span></span> <span data-ttu-id="b6b01-109">**SSIS ツールボックス**からサンプルにアクセスするには、説明の下に表示される **[サンプルの検索]** リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6b01-109">To access the samples from the **SSIS Toolbox**, click the **Find Samples** link that appears below the description.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6b01-110">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]の以前のバージョンとは異なり、ツールボックスからインストールされたコンポーネントは削除できません。</span><span class="sxs-lookup"><span data-stu-id="b6b01-110">Unlike previous versions of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], you cannot remove installed components from the toolbox.</span></span>  
  
 <span data-ttu-id="b6b01-111">**SSIS ツールボックス**では、制御フローとデータ フローのコンポーネントがカテゴリ別にまとめられています。</span><span class="sxs-lookup"><span data-stu-id="b6b01-111">In the **SSIS Toolbox**, control flow and data flow components are organized into categories.</span></span>  <span data-ttu-id="b6b01-112">カテゴリの表示を展開したり折りたたんだりでき、必要に応じてコンポーネントを編成できます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-112">You can expand and collapse categories for viewing and you can change the organization of components according to your preferences.</span></span>  <span data-ttu-id="b6b01-113">ツールボックスの内側を右クリックして **[既定のツールボックスの復元]** をクリックすると、既定の編成に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-113">You can restore the default organization, by right-clicking inside the toolbox and then click **Restore Toolbox Defaults**.</span></span>  
  
 <span data-ttu-id="b6b01-114">**[制御フロー]** タブ、 **[データ フロー]** タブ、および **[イベント ハンドラー]** タブを選択すると、 **[お気に入り]** カテゴリおよび **[共通]** カテゴリがツールボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-114">The **Favorites** and **Common** categories appear in the toolbox when you select the **Control Flow**, **Data Flow**, and **Event Handlers** tabs.</span></span> <span data-ttu-id="b6b01-115">[**制御フロー** ] タブまたは [**イベントハンドラー** ] タブを選択すると、[**その他のタスク**] カテゴリがツールボックスに表示されます。[**データフロー** ] タブを選択すると、**他の変換**、**他の変換元**、およびその他の変換**先**カテゴリがツールボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-115">The **Other Tasks** category appears in the toolbox when you select the **Control Flow** tab or the **Event Handlers** tab. The **Other Transforms**, **Other Sources**, and **Other Destinations** categories appear in the toolbox when you select the **Data Flow** tab.</span></span>  
  
 <span data-ttu-id="b6b01-116">新しい SSIS プロジェクトを作成するか、既存のプロジェクトを開くと、 **SSIS ツールボックス** が自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-116">When you create a new SSIS project or open an existing project, the **SSIS Toolbox** is automatically displayed.</span></span> <span data-ttu-id="b6b01-117">ツールボックスは、パッケージ デザイン画面の右上端にあるツールボックス ボタンをクリックして開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-117">You can also open the toolbox by clicking the toolbox button that is located in the top-right corner of the package design surface.</span></span>  
  
 <span data-ttu-id="b6b01-118">ツールボックスをドッキングしたり、ドッキング時には折りたたまれるように設定したり、ツールボックスを閉じたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="b6b01-118">You can dock the toolbox, set it to collapse when docked, and you can close the toolbox.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b6b01-119">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="b6b01-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b6b01-120">SSIS ツールボックス アイテムを移動する</span><span class="sxs-lookup"><span data-stu-id="b6b01-120">Move SSIS Toolbox Items</span></span>](../../2014/integration-services/move-ssis-toolbox-items.md)  
  
  
