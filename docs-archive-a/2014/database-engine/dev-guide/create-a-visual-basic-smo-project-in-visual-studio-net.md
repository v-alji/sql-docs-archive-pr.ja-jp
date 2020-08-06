---
title: Visual Studio .NET で Visual Basic SMO プロジェクトを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic [SMO]
ms.assetid: d7a3892c-0f1c-4c4d-8480-b58dce3720bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 844d27ab6aadbc972c6282c79adb13e15d55c322
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742546"
---
# <a name="create-a-visual-basic-smo-project-in-visual-studio-net"></a><span data-ttu-id="1b900-102">Visual Studio .NET での Visual Basic SMO プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="1b900-102">Create a Visual Basic SMO Project in Visual Studio .NET</span></span>
  <span data-ttu-id="1b900-103">このセクションでは、簡単な SMO コンソール アプリケーションを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b900-103">This section describes how to build a simple SMO console application.</span></span>  
  
 <span data-ttu-id="1b900-104">この例では、プログラムが SMO の型を参照できるように、名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="1b900-104">This example imports namespaces, which enables the program to reference SMO types.</span></span> <span data-ttu-id="1b900-105">`Agent` 名前空間のインポートは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1b900-105">The import of the `Agent` namespace is optional.</span></span> <span data-ttu-id="1b900-106">エージェントを使用するプログラムを作成するときに使用し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="1b900-106">Use it when you are writing a program that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="1b900-107">`Common` 名前空間は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへのセキュリティで保護された接続を確立するために必要です。</span><span class="sxs-lookup"><span data-stu-id="1b900-107">The `Common` namespace is required to establish a secure connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1b900-108">`SqlClient` 名前空間は、SQL 例外エラーの処理を行うために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1b900-108">The `SqlClient` namespace is used to process SQL exception errors.</span></span>  
  
### <a name="creating-a-visual-basic-smo-project-in-visual-studionet"></a><span data-ttu-id="1b900-109">Visual Studio .NET での Visual Basic SMO プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="1b900-109">Creating a Visual Basic SMO project in Visual Studio.NET</span></span>  
  
1.  <span data-ttu-id="1b900-110">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] または [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] を起動します。</span><span class="sxs-lookup"><span data-stu-id="1b900-110">Start [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (or [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).</span></span>  
  
2.  <span data-ttu-id="1b900-111">**[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b900-111">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="1b900-112">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b900-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="1b900-113">[**プロジェクトの種類**] ダイアログボックスで、[ **Visual Basic**] を選択し、[ **Windows**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b900-113">In **Project Types** dialog box, select **Visual Basic**, and then select **Windows**.</span></span> <span data-ttu-id="1b900-114">[ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] インストールされたテンプレート] ペインで、[**コンソールアプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b900-114">In the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installed Templates pane, select **Console Application.**</span></span>  
  
4.  <span data-ttu-id="1b900-115">Optional[**名前**] フィールドに、新しいアプリケーションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="1b900-115">(Optional) In the **Name** field, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="1b900-116">[ **OK** ] をクリックして、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] コンソールアプリケーションテンプレートを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1b900-116">Click **OK** to load the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] console application template.</span></span>  
  
6.  <span data-ttu-id="1b900-117">**[プロジェクト]** メニューの **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1b900-117">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="1b900-118">**[参照の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1b900-118">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="1b900-119">[**参照**] をクリックし、C:\Program Server\120\SDK\Assemblies フォルダー内の SMO アセンブリを見つけて、次のファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="1b900-119">Click **Browse**, locate the SMO assemblies in the C:\Program Files\Microsoft SQL Server\120\SDK\Assemblies folder, and then select the following files.</span></span> <span data-ttu-id="1b900-120">これらは、SMO アプリケーションのビルドに最低限必要なファイルです。</span><span class="sxs-lookup"><span data-stu-id="1b900-120">These are the minimum files that are required to build an SMO application:</span></span>  
  
     <span data-ttu-id="1b900-121">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="1b900-121">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
     <span data-ttu-id="1b900-122">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="1b900-122">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
     <span data-ttu-id="1b900-123">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="1b900-123">Microsoft.SqlServer.Smo.dll</span></span>  
  
     <span data-ttu-id="1b900-124">Microsoft.SqlServer.Management.Sdk.Sfc</span><span class="sxs-lookup"><span data-stu-id="1b900-124">Microsoft.SqlServer.Management.Sdk.Sfc</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1b900-125">複数の `Ctrl` ファイルを選択するには、キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b900-125">Use the `Ctrl` key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="1b900-126">必要に応じて任意の SMO アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="1b900-126">Add any additional SMO assemblies that are required.</span></span> <span data-ttu-id="1b900-127">たとえば、[!INCLUDE[ssSB](../../includes/sssb-md.md)] に特化したプログラミングを行っている場合は、以下のアセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="1b900-127">For example, if you are specifically programming [!INCLUDE[ssSB](../../includes/sssb-md.md)], add the following assemblies:</span></span>  
  
     <span data-ttu-id="1b900-128">Microsoft.SqlServer.ServiceBrokerEmum.dll</span><span class="sxs-lookup"><span data-stu-id="1b900-128">Microsoft.SqlServer.ServiceBrokerEmum.dll</span></span>  
  
9. <span data-ttu-id="1b900-129">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b900-129">Click **Open**.</span></span>  
  
10. <span data-ttu-id="1b900-130">[**表示**] メニューの [**コード**] をクリックするか、module1.vb ウィンドウを選択してコードウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="1b900-130">On the **View** menu, click **Code**.-Or-Select the Module1.vb window to show the code window.</span></span>  
  
11. <span data-ttu-id="1b900-131">コードでは、宣言の前に、次の**Imports**ステートメントを入力して、SMO 名前空間の型を修飾します。</span><span class="sxs-lookup"><span data-stu-id="1b900-131">In the code, before any declarations, type the following **Imports** statements to qualify the types in the SMO namespace.</span></span>  
  
    ```  
    Imports Microsoft.SqlServer.Management.Smo  
    Imports Microsoft.SqlServer.Management.Common  
    ```  
  
12. <span data-ttu-id="1b900-132">SMO では、Microsoft.SqlServer.Management.Smo の下に、Microsoft.SqlServer.Management.Smo.Agent などのさまざまな名前空間があります。</span><span class="sxs-lookup"><span data-stu-id="1b900-132">SMO has various namespaces under Microsoft.SqlServer.Management.Smo, such as Microsoft.SqlServer.Management.Smo.Agent.</span></span> <span data-ttu-id="1b900-133">これらの名前空間は、必要に応じて追加します。</span><span class="sxs-lookup"><span data-stu-id="1b900-133">Add these namespaces as they are required.</span></span>  
  
13. <span data-ttu-id="1b900-134">SMO コードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="1b900-134">You can now add your SMO code.</span></span>  
  
  
