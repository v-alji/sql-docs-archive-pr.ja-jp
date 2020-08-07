---
title: 'レッスン 1: Web サービスクライアントプロジェクトの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0070daa6-56b0-4663-83b2-44c96acafad8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: eda9413867c4ca6d44a5cf98b82be9bddc04d0f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719101"
---
# <a name="lesson-1-creating-the-web-service-client-project"></a><span data-ttu-id="b9a0e-102">レッスン 1: Web サービス クライアント プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="b9a0e-102">Lesson 1: Creating the Web Service Client Project</span></span>
  <span data-ttu-id="b9a0e-103">このチュートリアルでは、レポート サーバー Web サービスにアクセスする簡単なコンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-103">For this walkthrough, you will create a simple console application that accesses the Report Server Web service.</span></span> <span data-ttu-id="b9a0e-104">ここでは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で開発することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-104">This walkthrough assumes you are developing in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
### <a name="to-create-a-console-application"></a><span data-ttu-id="b9a0e-105">コンソール アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="b9a0e-105">To create a console application</span></span>  
  
1.  <span data-ttu-id="b9a0e-106">[**ファイル**] メニューの [**新規作成**] をポイントし、[**プロジェクト**] をクリックして [**新しいプロジェクト**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-106">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="b9a0e-107">左側のウィンドウの [**インストールされたテンプレート**] で、[ **Visual Basic** ] または [ **Visual C#** ] ノードをクリックし、展開された一覧からプロジェクトの種類のカテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-107">In the left pane, under **Installed Templates**, click either **Visual Basic** or the **Visual C#** node, and select a category of project types from the expanded list.</span></span>  
  
3.  <span data-ttu-id="b9a0e-108">[**コンソールアプリケーション**] プロジェクトの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-108">Choose the **Console Application** project type.</span></span>  
  
4.  <span data-ttu-id="b9a0e-109">[**名前**] ボックスに、プロジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-109">In the **Name** box, enter a name for your project.</span></span> <span data-ttu-id="b9a0e-110">名前を入力 `GetPropertiesSample` します。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-110">Type the name `GetPropertiesSample`.</span></span>  
  
5.  <span data-ttu-id="b9a0e-111">[**場所**] ボックスにプロジェクトを保存する場所のパスを入力するか、[**参照**] をクリックしてフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-111">In the **Location** box, enter the path where you want to save your project, or click **Browse** to navigate to the folder.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="b9a0e-112">ソリューションエクスプローラーに、プロジェクトの折りたたまれたビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-112">A collapsed view of your project appears in Solution Explorer.</span></span>  
  
     <span data-ttu-id="b9a0e-113">ソリューションエクスプローラーで、プロジェクトノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-113">In Solution Explorer, expand the project node.</span></span> <span data-ttu-id="b9a0e-114">Program.cs (の場合は module1.vb) という既定の名前のファイル [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] がプロジェクトに追加されました。</span><span class="sxs-lookup"><span data-stu-id="b9a0e-114">A file with the default name of Program.cs (Module1.vb for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) has been added to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a0e-115">参照</span><span class="sxs-lookup"><span data-stu-id="b9a0e-115">See Also</span></span>  
 <span data-ttu-id="b9a0e-116">[レッスン 2: Web 参照の追加](../../2014/tutorials/lesson-2-adding-a-web-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b9a0e-116">[Lesson 2: Adding a Web Reference](../../2014/tutorials/lesson-2-adding-a-web-reference.md) </span></span>  
 [<span data-ttu-id="b9a0e-117">Visual Basic または Visual C&#35; &#40;SSRS チュートリアルを使用したレポートサーバー Web サービスへのアクセス&#41;</span><span class="sxs-lookup"><span data-stu-id="b9a0e-117">Accessing the Report Server Web Service Using Visual Basic or Visual C&#35; &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
