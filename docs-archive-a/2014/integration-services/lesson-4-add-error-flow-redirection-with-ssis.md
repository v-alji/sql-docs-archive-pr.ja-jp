---
title: 'レッスン 4: エラーフローリダイレクトの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5b1d1ff9abf59a6288d1b693fce5a6fb707a129b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741122"
---
# <a name="lesson-4-adding-error-flow-redirection"></a><span data-ttu-id="172ac-102">レッスン 4:エラー フロー リダイレクトの追加</span><span class="sxs-lookup"><span data-stu-id="172ac-102">Lesson 4: Adding Error Flow Redirection</span></span>
  <span data-ttu-id="172ac-103">変換プロセスで発生する可能性のあるエラーを処理するために、には、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 変換できないデータを処理する方法を、コンポーネントごと、および列ごとに決定する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="172ac-103">To handle errors that may occur in the transformation process, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] gives you the ability to decide on a per component and per column basis how to handle data that cannot be transformed.</span></span> <span data-ttu-id="172ac-104">特定の列で発生したエラーは無視し、変換に失敗した行全体をリダイレクトできます。または、この操作をコンポーネント単位で行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="172ac-104">You can choose to ignore a failure in certain columns, redirect the entire failed row, or just fail the component.</span></span> <span data-ttu-id="172ac-105">既定の構成では、エラーの発生時に [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のすべてのコンポーネントが変換に失敗したものと見なされます。</span><span class="sxs-lookup"><span data-stu-id="172ac-105">By default, all components in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] are configured to fail when errors occur.</span></span> <span data-ttu-id="172ac-106">つまり、1 つのコンポーネントの変換が失敗すると、パッケージの変換が失敗されたものと見なされ、以降の処理が中断されます。</span><span class="sxs-lookup"><span data-stu-id="172ac-106">Failing a component, in turn, causes the package to fail and all subsequent processing to stop.</span></span>  
  
 <span data-ttu-id="172ac-107">パッケージ全体の変換を中断する代わりに、変換エラーが発生したときに潜在的なエラー処理を行うように構成する方法があります。</span><span class="sxs-lookup"><span data-stu-id="172ac-107">Instead of letting failures stop package execution, it is good practice to configure and handle potential processing errors as they occur within the transformation.</span></span> <span data-ttu-id="172ac-108">エラーを無視してパッケージが確実に実行されるように設定することもできますが、多くの場合、失敗した行を別の処理フローにリダイレクトした方がよい結果が得られます。退避させたデータおよびエラーは後で検証し、再変換できます。</span><span class="sxs-lookup"><span data-stu-id="172ac-108">While you might choose to ignore failures to ensure your package runs successfully, it is often better to redirect the failed row to another processing path where the data and the error can be persisted, examined and reprocessed at a later time.</span></span>  
  
 <span data-ttu-id="172ac-109">このレッスンでは、 [「レッスン 3: ログの追加](lesson-3-add-logging-with-ssis.md)」で開発したパッケージのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="172ac-109">In this lesson, you will create a copy of the package that you developed in [Lesson 3: Adding Logging](lesson-3-add-logging-with-ssis.md).</span></span> <span data-ttu-id="172ac-110">この新しいパッケージを使用し、壊れたサンプル データ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="172ac-110">Working with this new package, you will create a corrupted version of one of the sample data files.</span></span> <span data-ttu-id="172ac-111">この破損ファイルは、パッケージを実行するときに変換エラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="172ac-111">The corrupted file will force a processing error to occur when you run the package.</span></span>  
  
 <span data-ttu-id="172ac-112">エラー データを処理するには、フラット ファイルの変換先を追加および構成し、Lookup Currency Key 変換で参照値が見つからなかった行をファイルに書き込むようにします。</span><span class="sxs-lookup"><span data-stu-id="172ac-112">To handle the error data, you will add and configure a Flat File destination that will write any rows that fail to locate a lookup value in the Lookup Currency Key transformation to a file.</span></span>  
  
 <span data-ttu-id="172ac-113">また、エラー データをファイルに書き込む前に、エラーの説明を取得するスクリプトを含むスクリプト コンポーネントを追加し、</span><span class="sxs-lookup"><span data-stu-id="172ac-113">Before the error data is written to the file, you will include a Script component that uses script to get error descriptions.</span></span> <span data-ttu-id="172ac-114">その後 Lookup Currency Key 変換を再構成して、処理できなかったデータをスクリプト変換にリダイレクトするようにします。</span><span class="sxs-lookup"><span data-stu-id="172ac-114">You will then reconfigure the Lookup Currency Key transformation to redirect any data that could not be processed to the Script transformation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="172ac-115">このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="172ac-115">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="172ac-116">**AdventureWorksDW2012**をインストールしてデプロイする方法の詳細については、 [CodePlex の Reporting Services Product Samples プロジェクト](https://go.microsoft.com/fwlink/p/?LinkId=526910)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="172ac-116">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples Project on CodePlex](https://go.microsoft.com/fwlink/p/?LinkId=526910).</span></span>  
  
## <a name="tasks-in-lesson"></a><span data-ttu-id="172ac-117">レッスンでの作業</span><span class="sxs-lookup"><span data-stu-id="172ac-117">Tasks in Lesson</span></span>  
 <span data-ttu-id="172ac-118">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="172ac-118">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="172ac-119">手順 1:レッスン 3 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="172ac-119">Step 1: Copying the Lesson 3 Package</span></span>](lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [<span data-ttu-id="172ac-120">手順 2:破損ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="172ac-120">Step 2: Creating a Corrupted File</span></span>](lesson-4-2-creating-a-corrupted-file.md)  
  
-   [<span data-ttu-id="172ac-121">手順 3:エラー フロー リダイレクトの追加</span><span class="sxs-lookup"><span data-stu-id="172ac-121">Step 3: Adding Error Flow Redirection</span></span>](lesson-4-3-adding-error-flow-redirection.md)  
  
-   [<span data-ttu-id="172ac-122">手順 4:フラット ファイル変換先の追加</span><span class="sxs-lookup"><span data-stu-id="172ac-122">Step 4: Adding a Flat File Destination</span></span>](lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [<span data-ttu-id="172ac-123">手順 5:レッスン 4 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="172ac-123">Step 5: Testing the Lesson 4 Tutorial Package</span></span>](lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="172ac-124">レッスンの開始</span><span class="sxs-lookup"><span data-stu-id="172ac-124">Start the Lesson</span></span>  
 [<span data-ttu-id="172ac-125">手順 1:レッスン 3 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="172ac-125">Step 1: Copying the Lesson 3 Package</span></span>](lesson-4-1-copying-the-lesson-3-package.md)  
  
  
