---
title: '手順 5: フラット ファイル ソースの追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 504cfb4bc722627eb8ee70ec1f2c562cef8f1f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641091"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a><span data-ttu-id="d9a45-102">手順 5:フラット ファイル ソースの追加と構成</span><span class="sxs-lookup"><span data-stu-id="d9a45-102">Step 5: Adding and Configuring the Flat File Source</span></span>
  <span data-ttu-id="d9a45-103">ここでは、フラット ファイル ソースをパッケージに追加し、構成します。</span><span class="sxs-lookup"><span data-stu-id="d9a45-103">In this task, you will add and configure a Flat File source to your package.</span></span> <span data-ttu-id="d9a45-104">フラット ファイル ソースとは、フラット ファイル接続マネージャーにより定義されるメタデータを使用するデータ フロー コンポーネントです。フラット ファイル接続マネージャーは、変換処理によってフラット ファイルから取得されるデータの形式や構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="d9a45-104">A Flat File source is a data flow component that uses metadata defined by a Flat File connection manager to specify the format and structure of the data to be extracted from the flat file by a transform process.</span></span> <span data-ttu-id="d9a45-105">フラット ファイル接続マネージャーに定義されているファイル形式を使用し、1 つのフラット ファイルからデータを取得するよう、フラット ファイル ソースを定義できます。</span><span class="sxs-lookup"><span data-stu-id="d9a45-105">The Flat File source can be configured to extract data from a single flat file by using the file format definition provided by the Flat File connection manager.</span></span>  
  
 <span data-ttu-id="d9a45-106">このチュートリアルでは、前に作成した接続マネージャーを使用するようにフラットファイルソースを構成し `Sample Flat File Source Data` ます。</span><span class="sxs-lookup"><span data-stu-id="d9a45-106">For this tutorial, you will configure the Flat File source to use the `Sample Flat File Source Data` connection manager that you previously created.</span></span>  
  
### <a name="to-add-a-flat-file-source-component"></a><span data-ttu-id="d9a45-107">フラット ファイル ソース コンポーネントを追加するには</span><span class="sxs-lookup"><span data-stu-id="d9a45-107">To add a Flat File Source component</span></span>  
  
1.  <span data-ttu-id="d9a45-108">**データフローデザイナーを**開きます。そのためには、データフロータスクをダブルクリックするか、[ `Extract Sample Currency Data` **データフロー] タブ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9a45-108">Open the **Data Flow** designer, either by double-clicking the `Extract Sample Currency Data` data flow task or by clicking the **Data Flow tab**.</span></span>  
  
2.  <span data-ttu-id="d9a45-109">**[SSIS ツールボックス]** で **[その他の変換元]** を展開し、 **[フラット ファイル ソース]** を **[データ フロー]** タブのデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d9a45-109">In the **SSIS Toolbox**, expand **OtherSources**, and then drag a **Flat File Source** onto the design surface of the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="d9a45-110">[**データフロー** ] デザイン画面で、新しく追加した**フラットファイルソース**を右クリックし **、[名前の変更]** をクリックして、名前をに変更し `Extract Sample Currency Data` ます。</span><span class="sxs-lookup"><span data-stu-id="d9a45-110">On the **Data Flow** design surface, right-click the newly added **Flat File Source**, click **Rename**, and change the name to `Extract Sample Currency Data`.</span></span>  
  
4.  <span data-ttu-id="d9a45-111">このフラット ファイル ソースをダブルクリックして、[フラット ファイル ソース エディター] ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="d9a45-111">Double-click the Flat File source to open the Flat File Source Editor dialog box.</span></span>  
  
5.  <span data-ttu-id="d9a45-112">[**フラットファイル接続マネージャー** ] ボックスで、を選択し `Sample Flat File Source Data` ます。</span><span class="sxs-lookup"><span data-stu-id="d9a45-112">In the **Flat file connection manager** box, select `Sample Flat File Source Data`.</span></span>  
  
6.  <span data-ttu-id="d9a45-113">**[列]** をクリックし、列名が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d9a45-113">Click **Columns** and verify that the names of the columns are correct.</span></span>  
  
7.  <span data-ttu-id="d9a45-114">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9a45-114">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="d9a45-115">[フラット ファイル ソース] を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d9a45-115">Right-click the Flat File source and click **Properties**.</span></span>  
  
9. <span data-ttu-id="d9a45-116">[プロパティウィンドウで、 `LocaleID` プロパティが**英語 (米国)** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d9a45-116">In the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d9a45-117">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="d9a45-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d9a45-118">手順 6:参照変換の追加と構成</span><span class="sxs-lookup"><span data-stu-id="d9a45-118">Step 6: Adding and Configuring the Lookup Transformations</span></span>](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="d9a45-119">参照</span><span class="sxs-lookup"><span data-stu-id="d9a45-119">See Also</span></span>  
 <span data-ttu-id="d9a45-120">[フラット ファイル ソース](data-flow/flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="d9a45-120">[Flat File Source](data-flow/flat-file-source.md) </span></span>  
 <span data-ttu-id="d9a45-121">[[フラット ファイル接続マネージャー エディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="d9a45-121">[Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md)</span></span>  
  
  
