---
title: '[あいまいグループ化変換エディター] ([接続マネージャー] タブ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2a8b0af9f36fdd386f7da375184fd4e4ec5c4be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644025"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a><span data-ttu-id="39b58-102">[あいまいグループ化変換エディター] ([接続マネージャー] タブ)</span><span class="sxs-lookup"><span data-stu-id="39b58-102">Fuzzy Grouping Transformation Editor (Connection Manager Tab)</span></span>
  <span data-ttu-id="39b58-103">**[あいまいグループ化変換エディター]** ダイアログ ボックスの **[接続マネージャー]** タブを使用すると、既存の接続を選択したり新しい接続を作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="39b58-103">Use the **Connection Manager** tab of the **Fuzzy Grouping Transformation Editor** dialog box to select an existing connection or create a new one.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39b58-104">接続によって指定されるサーバーでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b58-104">The server specified by the connection must be running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39b58-105">あいまいグループ化変換では、変換に対する完全な入力と同じサイズの一時データ オブジェクトが tempdb に作成されます。</span><span class="sxs-lookup"><span data-stu-id="39b58-105">The Fuzzy Grouping transformation creates temporary data objects in tempdb that may be as large as the full input to the transformation.</span></span> <span data-ttu-id="39b58-106">変換の実行中は、これらの一時オブジェクトに対してサーバー クエリが発行されます。</span><span class="sxs-lookup"><span data-stu-id="39b58-106">While the transformation executes, it issues server queries against these temporary objects.</span></span> <span data-ttu-id="39b58-107">この操作は、サーバーの全体のパフォーマンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39b58-107">This can affect overall server performance.</span></span>  
  
 <span data-ttu-id="39b58-108">あいまいグループ化変換の詳細については、「 [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b58-108">To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="39b58-109">オプション</span><span class="sxs-lookup"><span data-stu-id="39b58-109">Options</span></span>  
 <span data-ttu-id="39b58-110">**[キャッシュなし]**</span><span class="sxs-lookup"><span data-stu-id="39b58-110">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="39b58-111">既存の OLE DB 接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="39b58-111">Select an existing OLE DB connection manager by using the list box, or create a new connection by using the **New** button.</span></span>  
  
 <span data-ttu-id="39b58-112">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="39b58-112">**New**</span></span>  
 <span data-ttu-id="39b58-113">**[OLE DB 接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="39b58-113">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39b58-114">参照</span><span class="sxs-lookup"><span data-stu-id="39b58-114">See Also</span></span>  
 <span data-ttu-id="39b58-115">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="39b58-115">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="39b58-116">あいまいグループ化変換を使用して類似のデータ行を識別する</span><span class="sxs-lookup"><span data-stu-id="39b58-116">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
