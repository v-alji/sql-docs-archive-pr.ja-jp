---
title: キューブウィザードを使用してキューブを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], creating
ms.assetid: d46d659c-3a4e-4364-94ac-f5eb6ba0ec25
author: minewiskan
ms.author: owend
ms.openlocfilehash: 441c296c0fd71b2a9c2b8332743da6224839a471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737098"
---
# <a name="create-a-cube-using-the-cube-wizard"></a><span data-ttu-id="753fd-102">キューブ ウィザードを使用したキューブの作成</span><span class="sxs-lookup"><span data-stu-id="753fd-102">Create a Cube Using the Cube Wizard</span></span>
  <span data-ttu-id="753fd-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のキューブ ウィザードを使用すると、新しいキューブを作成できます。</span><span class="sxs-lookup"><span data-stu-id="753fd-103">You can create a new cube by using the Cube Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-a-new-cube"></a><span data-ttu-id="753fd-104">新しいキューブを作成するには</span><span class="sxs-lookup"><span data-stu-id="753fd-104">To create a new cube</span></span>  
  
1.  <span data-ttu-id="753fd-105">**ソリューション エクスプローラー**で **[キューブ]** を右クリックし、 **[新しいキューブ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753fd-105">In **Solution Explorer**, right-click **Cubes**, and then click **New Cube**.</span></span>  
  
2.  <span data-ttu-id="753fd-106">キューブ ウィザードの **[作成方法の選択]** ページで、 **[既存のテーブルの使用]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753fd-106">On the **Select Creation Method** page of the Cube Wizard, select **Use existing tables**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="753fd-107">既存のテーブルを使用せずにキューブを作成することが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="753fd-107">You might occasionally have to create a cube without using existing tables.</span></span> <span data-ttu-id="753fd-108">空のキューブを作成するには、 **[空のキューブの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="753fd-108">To create an empty cube, select **Create an empty cube**.</span></span> <span data-ttu-id="753fd-109">テーブルを生成するには、 **[データ ソースにテーブルを生成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="753fd-109">To generate tables, select **Generate tables in the data source**.</span></span>  
  
3.  <span data-ttu-id="753fd-110">**[メジャー グループ テーブルの選択]** ページで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="753fd-110">On the **Select Measure Group Tables** page, do the following procedures:</span></span>  
  
    1.  <span data-ttu-id="753fd-111">**[データ ソース ビュー]** ボックスの一覧で、データ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="753fd-111">In the **Data source view** list, select a data source view.</span></span>  
  
    2.  <span data-ttu-id="753fd-112">**[メジャー グループ テーブル]** ボックスの一覧で、メジャー グループの作成に使用するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="753fd-112">In the **Measure group tables** list, select the tables that will be used to create measure groups.</span></span>  
  
    3.  <span data-ttu-id="753fd-113">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753fd-113">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="753fd-114">**[メジャーの選択]** ページで、キューブに含めるメジャーを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753fd-114">On the **Select Measures** page, select the measures that you want to include in the cube, and then click **Next**.</span></span>  
  
     <span data-ttu-id="753fd-115">必要に応じて、メジャーとメジャー グループの名前を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="753fd-115">Optionally, you can change the names of the measures and measure groups.</span></span>  
  
5.  <span data-ttu-id="753fd-116">**[既存のディメンションの選択]** ページで、キューブに含める既存のディメンションを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753fd-116">On the **Select Existing Dimensions** page, select the existing dimensions to include in the cube, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="753fd-117">**[既存のディメンションの選択]** ページは、選択したいずれかのメジャー グループのデータベースにディメンションが既に存在している場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="753fd-117">The **Select Existing Dimensions** page appears if dimensions already exist in the database for any of the selected measure groups.</span></span>  
  
6.  <span data-ttu-id="753fd-118">**[新しいディメンションの選択]** ページで、作成する新しいディメンションを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753fd-118">On the **Select New Dimensions** page, select the new dimensions to create, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="753fd-119">**[新しいディメンションの選択]** ページは、どのテーブルもディメンション テーブルに適しており、テーブルが既存のディメンションによってまだ使用されていない場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="753fd-119">The **Select New Dimensions** page appears if any tables would be good candidates for dimension tables, and the tables have not already been used by existing dimensions.</span></span>  
  
7.  <span data-ttu-id="753fd-120">**[欠落したディメンション キーの選択]** ページで、ディメンションのキーを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753fd-120">On the **Select Missing Dimension Keys** page, select a key for the dimension, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="753fd-121">**[欠落したディメンション キーの選択]** ページは、指定したどのディメンション テーブルにも定義されたキーがない場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="753fd-121">The **Select Missing Dimension Keys** page appears if any of the dimension tables that you specified do not have a key defined.</span></span>  
  
8.  <span data-ttu-id="753fd-122">**[ウィザードの完了]** ページで、新しいキューブの名前を入力し、キューブ構造を確認します。</span><span class="sxs-lookup"><span data-stu-id="753fd-122">On the **Completing the Wizard** page, enter a name for the new cube and review the cube structure.</span></span> <span data-ttu-id="753fd-123">変更が必要な場合は **[戻る]** をクリックします。変更が必要ない場合は **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="753fd-123">If you want to make changes, click **Back**; otherwise, click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="753fd-124">キューブ ウィザードを完了した後、キューブ デザイナーを使用してキューブを構成できます。</span><span class="sxs-lookup"><span data-stu-id="753fd-124">You can use Cube Designer after you complete the Cube Wizard to configure the cube.</span></span> <span data-ttu-id="753fd-125">また、ディメンション デザイナーを使用して、作成したディメンションの属性と階層を追加、削除、および構成できます。</span><span class="sxs-lookup"><span data-stu-id="753fd-125">You can also use Dimension Designer to add, remove, and configure attributes and hierarchies in the dimensions that you created.</span></span>  
  
  
