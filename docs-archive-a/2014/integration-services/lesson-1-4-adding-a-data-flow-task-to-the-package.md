---
title: '手順 4: パッケージへのデータ フロー タスクの追加 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4fda1de99e9fcaa683f9063e2feb1b71886a5cd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641096"
---
# <a name="step-4-adding-a-data-flow-task-to-the-package"></a><span data-ttu-id="ddb40-102">手順 4:パッケージへのデータ フロー タスクの追加</span><span class="sxs-lookup"><span data-stu-id="ddb40-102">Step 4: Adding a Data Flow Task to the Package</span></span>
  <span data-ttu-id="ddb40-103">前の実習では、データ ソースおよび変換先データに接続するための接続マネージャーを作成しました。次の実習では、パッケージにデータ フロー タスクを追加します。</span><span class="sxs-lookup"><span data-stu-id="ddb40-103">After you have created the connection managers for the source and destination data, the next task is to add a Data Flow task to your package.</span></span> <span data-ttu-id="ddb40-104">データ フロー タスクには、変換元と変換先の間でデータを移動させるデータ フロー エンジンがカプセル化されており、データを移動する際に、変換、クリーン、修正を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ddb40-104">The Data Flow task encapsulates the data flow engine that moves data between sources and destinations, and provides the functionality for transforming, cleaning, and modifying data as it is moved.</span></span> <span data-ttu-id="ddb40-105">抽出、変換、読み込み (ETL) プロセスのほとんどが、このデータ フロー タスクで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ddb40-105">The Data Flow task is where most of the work of an extract, transform, and load (ETL) process occurs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="ddb40-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]制御フローからデータフローを分離します。</span><span class="sxs-lookup"><span data-stu-id="ddb40-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separates data flow from control flow.</span></span>  
  
### <a name="to-add-a-data-flow-task"></a><span data-ttu-id="ddb40-107">データ フロー タスクを追加するには</span><span class="sxs-lookup"><span data-stu-id="ddb40-107">To add a Data Flow task</span></span>  
  
1.  <span data-ttu-id="ddb40-108">**[制御フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ddb40-108">Click the **Control Flow** tab.</span></span>  
  
2.  <span data-ttu-id="ddb40-109">**[SSIS ツールボックス]** で **[お気に入り]** を展開し、 **[データ フロー タスク]** を **[制御フロー]** タブのデザイン画面上にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ddb40-109">In the **SSIS Toolbox**, expand **Favorites**, and drag a **Data Flow Task** onto the design surfaceof the **Control Flow** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ddb40-110">SSIS ツールボックスが表示されていない場合は、メイン メニューの [SSIS]、[SSIS ツールボックス] の順に選択し、SSIS ツールボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="ddb40-110">If the SSIS Toolbox isn't available, on the main menu select SSIS then SSIS Toolbox to display the SSIS Toolbox.</span></span>  
  
3.  <span data-ttu-id="ddb40-111">[**制御フロー** ] デザイン画面で、新しく追加した [**データフロータスク**] を右クリックし、[**名前の変更**] をクリックして、名前をに変更し `Extract Sample Currency Data` ます。</span><span class="sxs-lookup"><span data-stu-id="ddb40-111">On the **Control Flow** design surface, right-click the newly added **Data Flow Task**, click **Rename**, and change the name to `Extract Sample Currency Data`.</span></span>  
  
     <span data-ttu-id="ddb40-112">デザイン画面に追加するすべてのコンポーネントに一意な名前を付けるようにしましょう。</span><span class="sxs-lookup"><span data-stu-id="ddb40-112">It is good practice to provide unique names to all components that you add to a design surface.</span></span> <span data-ttu-id="ddb40-113">使いやすさと管理しやすさを考慮し、各コンポーネントの機能がわかるような名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="ddb40-113">For ease of use and maintainability, the names should describe the function that each component performs.</span></span> <span data-ttu-id="ddb40-114">このような方法で名前を付けておけば、自己文書化された [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ddb40-114">Following these naming guidelines allows your [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to be self-documenting.</span></span> <span data-ttu-id="ddb40-115">パッケージを文書化するには、注釈を使用する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="ddb40-115">Another way to document your packages is by using annotations.</span></span> <span data-ttu-id="ddb40-116">注釈の詳細については、「[パッケージで注釈を使用する](use-annotations-in-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddb40-116">For more information about annotations, see [Use Annotations in Packages](use-annotations-in-packages.md).</span></span>  
  
4.  <span data-ttu-id="ddb40-117">データフロータスクを右クリックし、[**プロパティ**] をクリックします。プロパティウィンドウで、 `LocaleID` プロパティが**英語 (米国)** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ddb40-117">Right-click the Data Flow task, click **Properties**, and in the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ddb40-118">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="ddb40-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ddb40-119">手順 5:フラット ファイル ソースの追加と構成</span><span class="sxs-lookup"><span data-stu-id="ddb40-119">Step 5: Adding and Configuring the Flat File Source</span></span>](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="ddb40-120">参照</span><span class="sxs-lookup"><span data-stu-id="ddb40-120">See Also</span></span>  
 [<span data-ttu-id="ddb40-121">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="ddb40-121">Data Flow Task</span></span>](control-flow/data-flow-task.md)  
  
  
