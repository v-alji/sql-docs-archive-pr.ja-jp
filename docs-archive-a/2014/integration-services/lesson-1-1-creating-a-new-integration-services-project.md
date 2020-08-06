---
title: '手順 1: 新しい Integration Services プロジェクトの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d6d16d7febcdecb01eb7a93167c2a18d225a9c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641109"
---
# <a name="step-1-creating-a-new-integration-services-project"></a><span data-ttu-id="374f7-102">手順 1:新しい Integration Services プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="374f7-102">Step 1: Creating a New Integration Services Project</span></span>
  <span data-ttu-id="374f7-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] でパッケージを作成するには、まず [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="374f7-103">The first step in creating a package in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is to create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="374f7-104">このプロジェクトには、データ変換ソリューションで使用するオブジェクト (データ ソース、データ ソース ビュー、パッケージ) のテンプレートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="374f7-104">This project includes the templates for the objects - data sources, data source views, and packages - that you use in a data transformation solution.</span></span>  
  
 <span data-ttu-id="374f7-105">この [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] チュートリアルで作成するパッケージは、ロケール依存型データの値を解釈します。</span><span class="sxs-lookup"><span data-stu-id="374f7-105">The packages that you will create in this [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorial interpret the values of locale-sensitive data.</span></span> <span data-ttu-id="374f7-106">コンピューターが地域オプション [英語 (米国)] を使用するように構成されていない場合は、パッケージ内で追加のプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="374f7-106">If your computer is not configured to use the regional option English (United States), you need to set additional properties in the package.</span></span> <span data-ttu-id="374f7-107">レッスン 2 から 5 では、レッスン 1 で作成したパッケージをコピーして使用します。コピーしたパッケージでは、ロケール依存型のプロパティを更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="374f7-107">The packages that you use in lessons 2 through 5 are copied from the package created in lesson 1, and you need not update locale-sensitive properties in the copied packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="374f7-108">このチュートリアルには、Microsoft SQL Server Data Tools が必要です。</span><span class="sxs-lookup"><span data-stu-id="374f7-108">This tutorial requires Microsoft SQL Server Data Tools.</span></span>  
>   
>  <span data-ttu-id="374f7-109">SQL Server Data Tools のインストールの詳細については、「 [SQL Server Data Tools のダウンロード](https://msdn.microsoft.com/data/hh297027)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="374f7-109">For more information on installing the SQL Server Data Tools see [SQL Server Data Tools Download](https://msdn.microsoft.com/data/hh297027).</span></span>  
  
### <a name="to-create-a-new-integration-services-project"></a><span data-ttu-id="374f7-110">新しい Integration Services プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="374f7-110">To create a new Integration Services project</span></span>  
  
1.  <span data-ttu-id="374f7-111">**[スタート]** メニューで、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントし、 **[SQL Server Data Tools]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="374f7-111">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, and click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="374f7-112">新しい **プロジェクトを作成するため、** [ファイル] **メニューの**[新規作成] **をポイントし、** [プロジェクト] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="374f7-112">On the **File** menu, point to **New**, and click **Project** to create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
3.  <span data-ttu-id="374f7-113">**[新しいプロジェクト]** ダイアログ ボックスの **[インストールされているテンプレート]** で **[ビジネス インテリジェンス]** を展開し、 **[テンプレート]** ペインで **[Integration Services プロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="374f7-113">In the **New Project** dialog box, expand the **Business Intelligence** node under **Installed Templates**, and select **Integration Services Project** in the **Templates** pane.</span></span>  
  
4.  <span data-ttu-id="374f7-114">**[名前]** ボックスに表示されている既定の名前を「 **SSIS Tutorial**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="374f7-114">In the **Name** box, change the default name to **SSIS Tutorial**.</span></span> <span data-ttu-id="374f7-115">必要に応じて、 **[ソリューションのディレクトリを作成]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="374f7-115">Optionally, clear the **Create directory for solution** check box.</span></span>  
  
5.  <span data-ttu-id="374f7-116">既定の場所をそのまま使用するか、 **[参照]** をクリックして使用するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="374f7-116">Accept the default location, or click **Browse** to browse to locate the folder you want to use.</span></span> <span data-ttu-id="374f7-117">**[プロジェクトの場所]** ダイアログ ボックスで、目的のフォルダーをクリックして **[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="374f7-117">In the **Project Location** dialog box, click the folder and click **Select Folder**.</span></span>  
  
6.  <span data-ttu-id="374f7-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="374f7-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="374f7-119">既定では、 **Package.dtsx**という名前の空のパッケージが作成され、SSIS パッケージの下のプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="374f7-119">By default, an empty package, titled **Package.dtsx**, will be created and added to your project under SSIS Packages.</span></span>  
  
7.  <span data-ttu-id="374f7-120">**ソリューション エクスプローラー** で **[Package.dtsx]** を右クリックし、 **[名前の変更]** をクリックします。表示されている既定のパッケージ名を「 **Lesson 1.dtsx**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="374f7-120">In **Solution Explorer** toolbar, right-click **Package.dtsx**, click **Rename**, and rename the default package to **Lesson 1.dtsx**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="374f7-121">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="374f7-121">Next Task in Lesson</span></span>  
 [<span data-ttu-id="374f7-122">手順 2:フラット ファイル接続マネージャーの追加と構成</span><span class="sxs-lookup"><span data-stu-id="374f7-122">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  
