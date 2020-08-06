---
title: 'レッスン 5: パッケージ配置モデルのパッケージ構成の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ee03d624ac7144cf6aef0829bcb7835fe5af9c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713305"
---
# <a name="lesson-5-adding-package-configurations-for-the-package-deployment-model"></a><span data-ttu-id="02a49-102">レッスン 5: パッケージ配置モデルのパッケージ構成の追加</span><span class="sxs-lookup"><span data-stu-id="02a49-102">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>
  <span data-ttu-id="02a49-103">パッケージ構成を使用すれば、開発環境の外部からランタイムのプロパティと変数を設定できます。</span><span class="sxs-lookup"><span data-stu-id="02a49-103">Package configurations let you set run-time properties and variables from outside of the development environment.</span></span> <span data-ttu-id="02a49-104">この構成により、配置と配信が容易で柔軟なパッケージを開発できます。</span><span class="sxs-lookup"><span data-stu-id="02a49-104">Configurations allow you to develop packages that are flexible and easy to both deploy and distribute.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="02a49-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、次の種類の構成が用意されています。</span><span class="sxs-lookup"><span data-stu-id="02a49-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offers the following configuration types:</span></span>  
  
-   <span data-ttu-id="02a49-106">XML 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="02a49-106">XML configuration file</span></span>  
  
-   <span data-ttu-id="02a49-107">環境変数</span><span class="sxs-lookup"><span data-stu-id="02a49-107">Environment variable</span></span>  
  
-   <span data-ttu-id="02a49-108">レジストリ エントリ</span><span class="sxs-lookup"><span data-stu-id="02a49-108">Registry entry</span></span>  
  
-   <span data-ttu-id="02a49-109">親パッケージ変数</span><span class="sxs-lookup"><span data-stu-id="02a49-109">Parent package variable</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="02a49-110">テーブル</span><span class="sxs-lookup"><span data-stu-id="02a49-110">table</span></span>  
  
 <span data-ttu-id="02a49-111">このレッスンでは、「 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 」で作成した単純な [ssISnoversion](lesson-4-add-error-flow-redirection-with-ssis.md) パッケージを変更し、パッケージ配置モデルを使用してパッケージの構成を利用します。</span><span class="sxs-lookup"><span data-stu-id="02a49-111">In this lesson, you will modify the simple [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you created in [Lesson 4: Adding Error Flow Redirection](lesson-4-add-error-flow-redirection-with-ssis.md) to use the Package Deployment Model and take advantage of package configurations.</span></span> <span data-ttu-id="02a49-112">またチュートリアルに含まれている、レッスン 4 を完了した状態のパッケージをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="02a49-112">You can also copy the completed Lesson 4 package that is included with the tutorial.</span></span> <span data-ttu-id="02a49-113">パッケージ構成ウィザードを使用し、Foreach ループ コンテナーの `Directory` プロパティを更新する XML 構成を作成します。具体的には、Directory プロパティにマップされているパッケージ レベル変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="02a49-113">Using the Package Configuration Wizard, you will create an XML configuration that updates the `Directory` property of the Foreach Loop container by using a package-level variable mapped to the Directory property.</span></span> <span data-ttu-id="02a49-114">構成ファイルを作成したら、開発環境の外部から変数の値を修正し、修正したプロパティに新しいサンプル データ フォルダーを参照させます。</span><span class="sxs-lookup"><span data-stu-id="02a49-114">Once you have created the configuration file, you will modify the value of the variable from outside of the development environment and point the modified property to a new sample data folder.</span></span> <span data-ttu-id="02a49-115">パッケージを再度実行すると、構成ファイルによって変数の値が設定され、変数によってプロパティが更新され `Directory` ます。</span><span class="sxs-lookup"><span data-stu-id="02a49-115">When you run the package again, the configuration file populates the value of the variable, and the variable in turn updates the `Directory` property.</span></span> <span data-ttu-id="02a49-116">結果として、パッケージにハードコーディングされた元のフォルダーのファイルではなく、新しいデータ フォルダーのファイルに対してパッケージが繰り返し実行されます。</span><span class="sxs-lookup"><span data-stu-id="02a49-116">As a result, the package iterates through the files in the new data folder, rather than iterating through the files in the original folder that was hard-coded in the package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="02a49-117">このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="02a49-117">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="02a49-118">**AdventureWorksDW2012**をインストールして配置する方法の詳細については、 [CodePlex での Reporting Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkID=526910)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02a49-118">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples on CodePlex](https://go.microsoft.com/fwlink/?LinkID=526910).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="02a49-119">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="02a49-119">Lesson Tasks</span></span>  
 <span data-ttu-id="02a49-120">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="02a49-120">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="02a49-121">手順 1:レッスン 4 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="02a49-121">Step 1: Copying the Lesson 4 Package</span></span>](lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [<span data-ttu-id="02a49-122">手順 2:パッケージ構成の有効化と構成</span><span class="sxs-lookup"><span data-stu-id="02a49-122">Step 2: Enabling and Configuring Package Configurations</span></span>](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [<span data-ttu-id="02a49-123">手順 3:Directory プロパティの構成値の変更</span><span class="sxs-lookup"><span data-stu-id="02a49-123">Step 3: Modifying the Directory Property Configuration Value</span></span>](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [<span data-ttu-id="02a49-124">手順 4:レッスン 5 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="02a49-124">Step 4: Testing the Lesson 5 Tutorial Package</span></span>](lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="02a49-125">レッスンの開始</span><span class="sxs-lookup"><span data-stu-id="02a49-125">Start the Lesson</span></span>  
  
-   [<span data-ttu-id="02a49-126">手順 1:レッスン 4 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="02a49-126">Step 1: Copying the Lesson 4 Package</span></span>](lesson-5-1-copying-the-lesson-4-package.md)  
  
  
