---
title: Visual Studio .NET で Visual C# SMO プロジェクトを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
ms.openlocfilehash: b78820fafd37675332e6703cabbb87e78bde5864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642727"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a><span data-ttu-id="3729b-102">Visual Studio .NET での Visual C# SMO プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3729b-102">Create a Visual C# SMO Project in Visual Studio .NET</span></span>
  <span data-ttu-id="3729b-103">このセクションでは、簡単な SMO コンソール アプリケーションを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3729b-103">This section describes how to build a simple SMO console application.</span></span>  
  
 <span data-ttu-id="3729b-104">この例では、プログラムが SMO の型を参照できるように、名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="3729b-104">This example imports namespaces, which enables the program to reference SMO types.</span></span> <span data-ttu-id="3729b-105">`Agent` 名前空間のインポートは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3729b-105">The import of the `Agent` namespace is optional.</span></span> <span data-ttu-id="3729b-106">エージェントを使用するプログラムを作成するときに使用し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3729b-106">Use it when you are writing a program that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="3729b-107">`Common` 名前空間は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへのセキュリティで保護された接続を確立するために必要です。</span><span class="sxs-lookup"><span data-stu-id="3729b-107">The `Common` namespace is required to establish a secure connection to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3729b-108">`SqlClient` 名前空間は、SQL 例外エラーの処理を行うために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3729b-108">The `SqlClient` namespace is used to process SQL exception errors.</span></span>  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a><span data-ttu-id="3729b-109">Visual C# SMO プロジェクトを Visual Studio.NET で作成する</span><span class="sxs-lookup"><span data-stu-id="3729b-109">Creating a Visual C# SMO project in Visual Studio.NET</span></span>  
  
1.  <span data-ttu-id="3729b-110">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] または [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] を起動します。</span><span class="sxs-lookup"><span data-stu-id="3729b-110">Start [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (or [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).</span></span>  
  
2.  <span data-ttu-id="3729b-111">**[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3729b-111">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="3729b-112">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3729b-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="3729b-113">[**プロジェクトの種類**] ダイアログボックスで、[ **Visual C#**] を選択し、[ **Windows**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3729b-113">In **Project Types** dialog box, select **Visual C#**, and then select **Windows**.</span></span> <span data-ttu-id="3729b-114">[ [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] インストールされたテンプレート] ペインで、[ **Windows アプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3729b-114">In the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Installed Templates pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="3729b-115">Optional[**名前**] フィールドに、新しいアプリケーションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="3729b-115">(Optional) In the **Name** field, type the name of the new application</span></span>  
  
5.  <span data-ttu-id="3729b-116">Visual C# アプリケーションの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="3729b-116">Select the Visual C# application type.</span></span> <span data-ttu-id="3729b-117">次の例では、[**コンソールアプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3729b-117">For the examples that follow, select **Console Application**.</span></span>  
  
6.  <span data-ttu-id="3729b-118">**[プロジェクト]** メニューの **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3729b-118">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="3729b-119">**[参照の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3729b-119">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="3729b-120">[**参照**] をクリックし、フォルダー内の SMO アセンブリを見つけ [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] て、次のファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3729b-120">Click **Browse**, locate the SMO assemblies in the [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] folder, and then select the following files.</span></span> <span data-ttu-id="3729b-121">これらは、SMO アプリケーションのビルドに最低限必要なファイルです。</span><span class="sxs-lookup"><span data-stu-id="3729b-121">These are the minimum files that are required to build an SMO application:</span></span>  
  
     <span data-ttu-id="3729b-122">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="3729b-122">Microsoft.SqlServer.ConnectionInfo.dll</span></span>  
  
     <span data-ttu-id="3729b-123">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="3729b-123">Microsoft.SqlServer.Smo.dll</span></span>  
  
     <span data-ttu-id="3729b-124">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="3729b-124">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span>  
  
     <span data-ttu-id="3729b-125">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="3729b-125">Microsoft.SqlServer.SqlEnum.dll</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3729b-126">複数の `Ctrl` ファイルを選択するには、キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="3729b-126">Use the `Ctrl` key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="3729b-127">必要に応じて任意の SMO アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="3729b-127">Add any additional SMO assemblies that are required.</span></span> <span data-ttu-id="3729b-128">たとえば、[!INCLUDE[ssSB](../../includes/sssb-md.md)] に特化したプログラミングを行っている場合は、以下のアセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="3729b-128">For example, if you are specifically programming [!INCLUDE[ssSB](../../includes/sssb-md.md)], add the following assemblies:</span></span>  
  
     <span data-ttu-id="3729b-129">Microsoft.SqlServer.ServiceBrokerEmum.dll</span><span class="sxs-lookup"><span data-stu-id="3729b-129">Microsoft.SqlServer.ServiceBrokerEmum.dll</span></span>  
  
9. <span data-ttu-id="3729b-130">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3729b-130">Click **Open**.</span></span>  
  
10. <span data-ttu-id="3729b-131">[**表示**] メニューの [**コード**] をクリックします。または、[Program1.cs [Design]] ウィンドウを選択し、windows フォームをダブルクリックしてコードウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="3729b-131">On the **View** menu, click **Code**.-Or-Select the Program1.cs [Design] Windows and double-click the windows form to show the code window.</span></span>  
  
11. <span data-ttu-id="3729b-132">コードでは、名前空間ステートメントの前に、次の `using` ステートメントを入力し、SMO 名前空間の型を修飾します。</span><span class="sxs-lookup"><span data-stu-id="3729b-132">In the code, before the namespace statement, type the following `using` statements to qualify the types in the SMO namespace:</span></span>  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. <span data-ttu-id="3729b-133">SMO では、Microsoft.SqlServer.Management.Smo の下に、Microsoft.SqlServer.Management.Smo.Agent などのさまざまな名前空間があります。</span><span class="sxs-lookup"><span data-stu-id="3729b-133">SMO has various namespaces under Microsoft.SqlServer.Management.Smo, such as Microsoft.SqlServer.Management.Smo.Agent.</span></span> <span data-ttu-id="3729b-134">これらの名前空間は、必要に応じて追加します。</span><span class="sxs-lookup"><span data-stu-id="3729b-134">Add these namespaces as they are required.</span></span>  
  
13. <span data-ttu-id="3729b-135">SMO コードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="3729b-135">You can now add your SMO code.</span></span>  
  
  
