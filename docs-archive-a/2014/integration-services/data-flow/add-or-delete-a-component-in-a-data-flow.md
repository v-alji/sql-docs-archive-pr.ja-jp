---
title: データ フローでコンポーネントを追加または削除する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding components
- components [Integration Services], data flow
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f041258d2b66e7b8da540a842848ebf70f4ed5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713354"
---
# <a name="add-or-delete-a-component-in-a-data-flow"></a><span data-ttu-id="0e95f-102">データ フローでコンポーネントを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="0e95f-102">Add or Delete a Component in a Data Flow</span></span>
  <span data-ttu-id="0e95f-103">データ フロー コンポーネントとは、データ フロー内の変換元、変換、および変換先のことです。</span><span class="sxs-lookup"><span data-stu-id="0e95f-103">Data flow components are sources, destinations, and transformations in a data flow.</span></span> <span data-ttu-id="0e95f-104">コンポーネントをデータ フローに追加するには、データ フロー タスクを事前にパッケージ制御フローに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e95f-104">Before you can add components to a data flow, the control flow in the package must include a Data Flow task.</span></span>  
  
 <span data-ttu-id="0e95f-105">次の手順では、パッケージのデータ フローでコンポーネントを追加または削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0e95f-105">The following procedures describe how to add or delete a component in the data flow of a package.</span></span>  
  
### <a name="to-add-a-component-to-a-data-flow"></a><span data-ttu-id="0e95f-106">データ フローにコンポーネントを追加するには</span><span class="sxs-lookup"><span data-stu-id="0e95f-106">To add a component to a data flow</span></span>  
  
1.  <span data-ttu-id="0e95f-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0e95f-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="0e95f-108">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="0e95f-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="0e95f-109">**[制御フロー]** タブをクリックし、コンポーネントを追加するデータ フローが含まれているデータ フロー タスクをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e95f-109">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow to which you want to add a component.</span></span>  
  
4.  <span data-ttu-id="0e95f-110">ツールボックスで、 **[データ フローの変換元]** 、 **[データ フロー変換]** 、または **[データ フローの変換先]** を展開し、次にデータ フロー アイテムを **[データ フロー]** タブのデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0e95f-110">In the Toolbox, expand **Data Flow Sources**, **Data Flow Transformations**, or **Data Flow Destinations**, and then drag a data flow item to the design surface of the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="0e95f-111">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e95f-111">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-component-from-a-data-flow"></a><span data-ttu-id="0e95f-112">データ フローからコンポーネントを削除するには</span><span class="sxs-lookup"><span data-stu-id="0e95f-112">To delete a component from a data flow</span></span>  
  
1.  <span data-ttu-id="0e95f-113">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0e95f-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="0e95f-114">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="0e95f-114">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="0e95f-115">**[制御フロー]** タブをクリックし、コンポーネントを削除するデータ フローが含まれているデータ フロー タスクをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e95f-115">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow from which you want to delete a component.</span></span>  
  
4.  <span data-ttu-id="0e95f-116">データ フロー コンポーネントを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e95f-116">Right-click the data flow component, and then click **Delete**.</span></span>  
  
5.  <span data-ttu-id="0e95f-117">削除操作を確認します。</span><span class="sxs-lookup"><span data-stu-id="0e95f-117">Confirm the delete operation.</span></span>  
  
6.  <span data-ttu-id="0e95f-118">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e95f-118">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e95f-119">参照</span><span class="sxs-lookup"><span data-stu-id="0e95f-119">See Also</span></span>  
 <span data-ttu-id="0e95f-120">[データ フロー内でコンポーネントを連結する](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="0e95f-120">[Connect Components in a Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="0e95f-121">[データフローコンポーネントでのエラー出力の構成](../configure-an-error-output-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="0e95f-121">[Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="0e95f-122">データ フロー</span><span class="sxs-lookup"><span data-stu-id="0e95f-122">Data Flow</span></span>](data-flow.md)  
  
  
