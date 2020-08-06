---
title: 変換元アシスタントを使用してソースを追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5e850b7c-4b89-42ad-b0a6-d63ac7cc9568
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b58b10508765580e0cffe9bd62099f3e2d69863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640224"
---
# <a name="add-a-source-using-source-assistant"></a><span data-ttu-id="e73fa-102">ソース アシスタントを使用してソースを追加する</span><span class="sxs-lookup"><span data-stu-id="e73fa-102">Add a Source using Source Assistant</span></span>
  <span data-ttu-id="e73fa-103">このトピックでは、変換元アシスタントを使用して新しい変換元を追加する手順について説明します。また、 **[新しい変換元の追加]** ダイアログで使用できるオプションも示します。このダイアログは、変換元アシスタントを SSIS デザイナーにドラッグ アンド ドロップしたときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e73fa-103">This topic provides steps to add a new source using the Source Assistant and also lists the options that are available on the **Add New Source** dialog, which you will see when you drag-drop the Source Assistant to the SSIS Designer.</span></span>  
  
### <a name="to-use-source-assistant-to-add-a-source"></a><span data-ttu-id="e73fa-104">変換元アシスタントを使用して変換元を追加するには</span><span class="sxs-lookup"><span data-stu-id="e73fa-104">To use Source Assistant to add a source</span></span>  
  
1.  <span data-ttu-id="e73fa-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、変換元コンポーネントを追加する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="e73fa-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you want to add a source component to.</span></span>  
  
2.  <span data-ttu-id="e73fa-106">**変換元アシスタント** コンポーネントを SSIS ツールボックスから **[データ フロー]** タブにドラッグします。 **[新しい変換元の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e73fa-106">Drag the **Source Assistant** component from the SSIS Toolbox to the **Data Flow** tab. You should see the **Add New Source** dialog box.</span></span> <span data-ttu-id="e73fa-107">次のセクションでは、ダイアログ ボックスで使用できるオプションについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="e73fa-107">The next section provides you details about the options available in the dialog box.</span></span>  
  
3.  <span data-ttu-id="e73fa-108">**[種類]** 一覧で、変換先の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="e73fa-108">Select the type of the destination in the **Types** list.</span></span>  
  
4.  <span data-ttu-id="e73fa-109">**[接続マネージャー]** 一覧で既存の接続マネージャーを選択するか、 **[\<New>]** を選択して新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e73fa-109">Select an existing connection manager in the **Connection Managers** list or select **\<New>** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="e73fa-110">既存の接続マネージャーを選択した場合は、 **[OK]** をクリックして **[新しい変換先の追加]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e73fa-110">If you select an existing connection manager, click **OK** to close the **Add New Destination** dialog box.</span></span> <span data-ttu-id="e73fa-111">変換先と接続マネージャーがデータ フローに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e73fa-111">You should see the destination and connection managers added to the data flow.</span></span>  
  
6.  <span data-ttu-id="e73fa-112">**[\<New>]** をクリックして新しい接続マネージャーを作成する場合は、 **[接続マネージャー]** ダイアログ ボックスが表示され、接続のパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e73fa-112">If you click **\<New>** to create a new connection manager, you should see a **Connection Manager** dialog box, which lets you specify parameters for the connection.</span></span> <span data-ttu-id="e73fa-113">新しい接続マネージャーの作成が完了すると、変換先と接続マネージャーが SSIS デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e73fa-113">After you are done with creating the new connection manager, you will see the destination and the connection manager in SSIS Designer.</span></span>  
  
  
