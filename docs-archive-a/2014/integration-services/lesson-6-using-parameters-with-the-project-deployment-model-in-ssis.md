---
title: 'レッスン 6: プロジェクト配置モデルでのパラメーターの使用 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4bdc6b9dfc019822d6cf1bd9ec7d89ffcc5ea5e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633890"
---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model"></a><span data-ttu-id="8b228-102">レッスン 6: プロジェクト配置モデルを持つパラメーターを使用する</span><span class="sxs-lookup"><span data-stu-id="8b228-102">Lesson 6: Using Parameters with the Project Deployment Model</span></span>
  <span data-ttu-id="8b228-103">SQL Server 2012 では、Integration Services サーバーにプロジェクトを配置できる新しい配置モデルが導入されています。</span><span class="sxs-lookup"><span data-stu-id="8b228-103">SQL Server 2012 introduces a new deployment model where you can deploy your projects to the Integration Services server.</span></span> <span data-ttu-id="8b228-104">Integration Services サーバーを使用すると、パッケージの管理、パッケージの実行、およびパッケージに合わせたランタイム値の構成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8b228-104">The Integration Services server enables you to manage and run packages, and to configure runtime values for packages.</span></span>  
  
 <span data-ttu-id="8b228-105">このレッスンでは、 [「レッスン 5: パッケージ配置モデルのパッケージ構成の追加](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)」で作成したパッケージを変更して、プロジェクト配置モデルを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="8b228-105">In this lesson, you will modify the package that you created in [Lesson 5: Adding Package Configurations for the Package Deployment Model](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) to use the Project Deployment Model.</span></span> <span data-ttu-id="8b228-106">構成値をパラメーターに置換して、サンプル データの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="8b228-106">You replace the configuration value with a parameter to specify the sample data location.</span></span> <span data-ttu-id="8b228-107">または、チュートリアルに含まれている、レッスン 5 を完了した状態のパッケージをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8b228-107">You can also copy the completed Lesson 5 package that is included with the tutorial.</span></span>  
  
 <span data-ttu-id="8b228-108">Integration Services プロジェクト構成ウィザードを使用して、プロジェクトをプロジェクト配置モデルに変換し、構成値ではなくパラメーターを使用してディレクトリ プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="8b228-108">Using the Integration Services Project Configuration Wizard, you will convert the project to the Project Deployment Model and use a Parameter rather than a configuration value to set the Directory property.</span></span> <span data-ttu-id="8b228-109">このレッスンでは、新規プロジェクト配置モデルに既存の SSIS パッケージを変換するための手順について部分的に説明します。</span><span class="sxs-lookup"><span data-stu-id="8b228-109">This lesson partially covers the steps you would follow to convert existing SSIS packages to the new Project Deployment Model.</span></span>  
  
 <span data-ttu-id="8b228-110">パッケージを再度実行すると、Integration Services サービスはパラメーターを使用して変数の値を生成します。さらに、この変数は Directory プロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="8b228-110">When you run the package again, the Integration Services service uses the parameter to populate the value of the variable, and the variable in turn updates the Directory property.</span></span> <span data-ttu-id="8b228-111">結果として、パッケージ構成ファイルで設定されたフォルダーではなく、パラメーター値によって指定された新しいデータ フォルダーのファイルに対してパッケージが繰り返し実行されます。</span><span class="sxs-lookup"><span data-stu-id="8b228-111">As a result, the package iterates through the files in the new data folder specified by the parameter value rather than the folder that was set in the package configuration file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8b228-112">このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="8b228-112">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="8b228-113">**AdventureWorksDW2012**をインストールおよび配置する方法の詳細については、「 [SQL Server のサンプルとサンプル データベースのインストールに関する注意点](https://technet.microsoft.com/library/ms161556%28v=sql.105%29)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b228-113">For more information about how to install and deploy **AdventureWorksDW2012**, see [Considerations for Installing SQL Server Samples and Sample Databases](https://technet.microsoft.com/library/ms161556%28v=sql.105%29).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="8b228-114">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="8b228-114">Lesson Tasks</span></span>  
 <span data-ttu-id="8b228-115">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8b228-115">This lesson contains the following tasks:</span></span>  
  
1.  [<span data-ttu-id="8b228-116">手順 1:レッスン 5 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="8b228-116">Step 1: Copying the Lesson 5 Package</span></span>](lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [<span data-ttu-id="8b228-117">手順 2:プロジェクトをプロジェクト配置モデルに変換する</span><span class="sxs-lookup"><span data-stu-id="8b228-117">Step 2: Converting the Project to the Project Deployment Model</span></span>](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [<span data-ttu-id="8b228-118">手順 3:レッスン 6 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="8b228-118">Step 3: Testing the Lesson 6 Package</span></span>](lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [<span data-ttu-id="8b228-119">手順 4:レッスン 6 のパッケージの展開</span><span class="sxs-lookup"><span data-stu-id="8b228-119">Step 4: Deploying the Lesson 6 Package</span></span>](lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="8b228-120">レッスンの開始</span><span class="sxs-lookup"><span data-stu-id="8b228-120">Start the Lesson</span></span>  
 [<span data-ttu-id="8b228-121">手順 1:レッスン 5 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="8b228-121">Step 1: Copying the Lesson 5 Package</span></span>](lesson-6-1-copying-the-lesson-5-package.md)  
  
  
