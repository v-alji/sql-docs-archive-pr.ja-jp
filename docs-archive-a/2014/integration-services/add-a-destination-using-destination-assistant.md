---
title: Destination Assistant | を使用して変換先を追加するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 747a0de0-3c2f-4d31-a692-7111fc0911d8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd36828a7bab7fb33b86765f9f064b6406a17a9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633277"
---
# <a name="add-a-destination-using-destination-assistant"></a><span data-ttu-id="a3fb4-102">デスティネーション アシスタントを使用して変換先を追加する</span><span class="sxs-lookup"><span data-stu-id="a3fb4-102">Add a Destination using Destination Assistant</span></span>
  <span data-ttu-id="a3fb4-103">このトピックでは、変換先アシスタントを使用して新しい変換先を追加する手順について説明します。また、 **[新しい変換先の追加]** ダイアログで使用できるオプションも示します。このダイアログは、変換先アシスタントを SSIS デザイナーにドラッグ アンド ドロップしたときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-103">This topic provides steps to add a new destination using the Destination Assistant and also lists the options that are available on the **Add New Destination** dialog, which you will see when you drag-drop the Destination Assistant to the SSIS Designer.</span></span>  
  
### <a name="to-use-destination-assistant-to-add-a-destination"></a><span data-ttu-id="a3fb4-104">変換先アシスタントを使用して変換先を追加するには</span><span class="sxs-lookup"><span data-stu-id="a3fb4-104">To use Destination Assistant to add a destination</span></span>  
  
1.  <span data-ttu-id="a3fb4-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、変換先コンポーネントを追加する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you want to add a destination component to.</span></span>  
  
2.  <span data-ttu-id="a3fb4-106">**変換先アシスタント** コンポーネントを SSIS ツールボックスから **[データ フロー]** タブにドラッグします。 **[新しい変換先の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-106">Drag the **Destination Assistant** component from the SSIS Toolbox to the **Data Flow** tab. You should see the **Add New Destination** dialog box.</span></span> <span data-ttu-id="a3fb4-107">次のセクションでは、ダイアログ ボックスで使用できるオプションについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-107">The next section provides you details about the options available in the dialog box.</span></span>  
  
3.  <span data-ttu-id="a3fb4-108">**[種類]** 一覧で、変換先の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-108">Select the type of the destination in the **Types** list.</span></span>  
  
4.  <span data-ttu-id="a3fb4-109">**[接続マネージャー]** 一覧で既存の接続マネージャーを選択するか、 **[\<New>]** を選択して新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-109">Select an existing connection manager in the **Connection Managers** list or select **\<New>** to create a new connection manager.</span></span>  
  
5.  <span data-ttu-id="a3fb4-110">既存の接続マネージャーを選択した場合は、 **[OK]** をクリックして **[新しい変換先の追加]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-110">If you select an existing connection manager, click **OK** to close the **Add New Destination** dialog box.</span></span> <span data-ttu-id="a3fb4-111">変換先と接続マネージャーがデータ フローに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-111">You should see the destination and connection managers added to the data flow.</span></span>  
  
6.  <span data-ttu-id="a3fb4-112">**[\<New>]** をクリックして新しい接続マネージャーを作成する場合は、 **[接続マネージャー]** ダイアログ ボックスが表示され、接続のパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-112">If you click **\<New>** to create a new connection manager, you should see a **Connection Manager** dialog box, which lets you specify parameters for the connection.</span></span> <span data-ttu-id="a3fb4-113">新しい接続マネージャーの作成が完了すると、変換先と接続マネージャーが SSIS デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3fb4-113">After you are done with creating the new connection manager, you will see the destination and the connection manager in SSIS Designer.</span></span>  
  
  
