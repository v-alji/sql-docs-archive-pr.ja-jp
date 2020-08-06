---
title: 変更の種類に応じた CDC ストリームのダイレクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a9b4e0c6a196669e4cedafcecf0477b228f3001
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633949"
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a><span data-ttu-id="08804-102">変更の種類に応じた CDC ストリームのダイレクト</span><span class="sxs-lookup"><span data-stu-id="08804-102">Direct the CDC Stream According to the Type of Change</span></span>
  <span data-ttu-id="08804-103">CDC スプリッター変換を追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクと 1 つの CDC ソースが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="08804-103">To add and configure a CDC splitter Transformation, the package must contain at least one Data Flow task and a CDC source.</span></span>  
  
 <span data-ttu-id="08804-104">パッケージに追加する CDC ソースでは、NetCDC 処理モードが選択されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="08804-104">The CDC source added to the package must have a NetCDC processing mode selected.</span></span> <span data-ttu-id="08804-105">処理モードの選択の詳細については、[「CDC ソース エディター ([接続マネージャー] ページ)」](../cdc-source-editor-connection-manager-page.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08804-105">For more information on selecting processing modes, see [CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md).</span></span>  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a><span data-ttu-id="08804-106">変更の種類に応じて CDC ストリームをダイレクトするには</span><span class="sxs-lookup"><span data-stu-id="08804-106">To direct the CDC stream according to the type of change</span></span>  
  
1.  <span data-ttu-id="08804-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="08804-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="08804-108">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="08804-108">In the Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="08804-109">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、CDC スプリッターをデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="08804-109">Click the **Data Flow** tab, and then from the **Toolbox**, drag the CDC splitter to the design surface.</span></span>  
  
4.  <span data-ttu-id="08804-110">パッケージに含まれている CDC ソースを CDC スプリッターに接続します。</span><span class="sxs-lookup"><span data-stu-id="08804-110">Connect the CDC source that is included in the package to the CDC Splitter.</span></span>  
  
5.  <span data-ttu-id="08804-111">CDC スプリッターを、1 つまたは複数の変換先に接続します。</span><span class="sxs-lookup"><span data-stu-id="08804-111">Connect the CDC splitter to one or more destinations.</span></span> <span data-ttu-id="08804-112">最大 3 つの出力に接続することができます。</span><span class="sxs-lookup"><span data-stu-id="08804-112">You can connect up to three different outputs.</span></span>  
  
6.  <span data-ttu-id="08804-113">以下の出力のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="08804-113">Select one of the following outputs:</span></span>  
  
    -   <span data-ttu-id="08804-114">削除出力: DELETE 変更行のダイレクト先の出力。</span><span class="sxs-lookup"><span data-stu-id="08804-114">Delete output: The output where DELETE change rows are directed.</span></span>  
  
    -   <span data-ttu-id="08804-115">挿入出力: INSERT 変更行のダイレクト先の出力。</span><span class="sxs-lookup"><span data-stu-id="08804-115">Insert output: The output where INSERT change rows are directed.</span></span>  
  
    -   <span data-ttu-id="08804-116">更新出力: 更新前および更新後の UPDATE 変更行と、Merge 変更行のダイレクト先の出力。</span><span class="sxs-lookup"><span data-stu-id="08804-116">Update output: The output where before/after UPDATE change rows and Merge change rows are directed.</span></span>  
  
7.  <span data-ttu-id="08804-117">必要に応じて、 **[詳細エディター]** ダイアログ ボックスを使用して、詳細なプロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="08804-117">Optionally, you can configure the advanced properties using the **Advanced Editor** dialog box.</span></span>  
  
     <span data-ttu-id="08804-118">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08804-118">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
     <span data-ttu-id="08804-119">**[詳細エディター]** ダイアログ ボックスを開くには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="08804-119">To open the **Advanced Editor** dialog box:</span></span>  
  
    -   <span data-ttu-id="08804-120">**プロジェクトの** [データ フロー] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 画面で、CDC スプリッターを右クリックし、 **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="08804-120">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC splitter and select **Show Advanced Editor**.</span></span>  
  
     <span data-ttu-id="08804-121">CDC スプリッターの使用方法の詳細については、「Microsoft SQL Server Integration Services の CDC コンポーネント」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08804-121">For more information about using the CDC splitter see CDC Components for Microsoft SQL Server Integration Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08804-122">参照</span><span class="sxs-lookup"><span data-stu-id="08804-122">See Also</span></span>  
 [<span data-ttu-id="08804-123">CDC スプリッター</span><span class="sxs-lookup"><span data-stu-id="08804-123">CDC Splitter</span></span>](cdc-splitter.md)  
  
  
