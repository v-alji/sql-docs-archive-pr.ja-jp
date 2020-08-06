---
title: データフローパスエディターを使用してパスのプロパティを設定する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 512249a4-83a6-4087-980d-a4344da48371
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e01565ef6cb70f3ac52187a6cc8d22d05508db4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742386"
---
# <a name="set-the-properties-of-a-path-by-using-the-data-flow-path-editor"></a><span data-ttu-id="6535d-102">データ フロー パス エディターを使用してパスのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="6535d-102">Set the Properties of a Path by Using the Data Flow Path Editor</span></span>
  <span data-ttu-id="6535d-103">パスは、2 つのデータ フロー コンポーネントを連結します。</span><span class="sxs-lookup"><span data-stu-id="6535d-103">Paths connect two data flow components.</span></span> <span data-ttu-id="6535d-104">パスのプロパティを設定する場合、データ フローには、2 つ以上の連結されたデータ フロー コンポーネントをあらかじめ含めておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="6535d-104">Before you can set path properties, the data flow must contain at least two connected data flow components.</span></span> <span data-ttu-id="6535d-105">詳細については、「 [データ フローでコンポーネントを追加または削除する](data-flow/add-or-delete-a-component-in-a-data-flow.md) 」と「 [データ フロー内でコンポーネントを連結する](data-flow/connect-components-in-a-data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6535d-105">For more information, see [Add or Delete a Component in a Data Flow](data-flow/add-or-delete-a-component-in-a-data-flow.md) and [Connect Components in a Data Flow](data-flow/connect-components-in-a-data-flow.md).</span></span>  
  
### <a name="to-set-path-properties"></a><span data-ttu-id="6535d-106">パスのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="6535d-106">To set path properties</span></span>  
  
1.  <span data-ttu-id="6535d-107">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="6535d-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="6535d-108">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="6535d-108">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="6535d-109">**[データ フロー]** タブをクリックし、パスをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6535d-109">Click the **Data Flow** tab, and then double-click a path.</span></span>  
  
4.  <span data-ttu-id="6535d-110">**[データ フロー パス エディター]** ダイアログ ボックスで、 **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6535d-110">In **Data Flow Path Editor**, click **General**.</span></span> <span data-ttu-id="6535d-111">ここで、パスの既定の名前を編集したり、パスに関する説明を入力できます。</span><span class="sxs-lookup"><span data-stu-id="6535d-111">You can then edit the default name of the path and provide a description of the path.</span></span> <span data-ttu-id="6535d-112">PathAnnotation プロパティを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="6535d-112">You can also modify the PathAnnotation property.</span></span>  
  
5.  <span data-ttu-id="6535d-113">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6535d-113">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="6535d-114">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6535d-114">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6535d-115">参照</span><span class="sxs-lookup"><span data-stu-id="6535d-115">See Also</span></span>  
 <span data-ttu-id="6535d-116">[Integration Services のパス](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="6535d-116">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="6535d-117">データ フロー</span><span class="sxs-lookup"><span data-stu-id="6535d-117">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
