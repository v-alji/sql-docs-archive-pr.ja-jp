---
title: データ フロー内でコンポーネントを連結する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8fc4a2fa81e9b110c27ea63b16d835d069bf12cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712254"
---
# <a name="connect-components-in-a-data-flow"></a><span data-ttu-id="38c10-102">データ フロー内でコンポーネントを連結する</span><span class="sxs-lookup"><span data-stu-id="38c10-102">Connect Components in a Data Flow</span></span>
  <span data-ttu-id="38c10-103">この手順は、データ フロー内のコンポーネントの出力を、同じデータ フロー内にある別のコンポーネントに連結する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="38c10-103">This procedure describes how to connect the output of components in a data flow to other components within the same data flow.</span></span>  
  
### <a name="to-connect-components-in-a-data-flow"></a><span data-ttu-id="38c10-104">データ フロー内でコンポーネントを連結するには</span><span class="sxs-lookup"><span data-stu-id="38c10-104">To connect components in a data flow</span></span>  
  
1.  <span data-ttu-id="38c10-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="38c10-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="38c10-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="38c10-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="38c10-107">**[制御フロー]** タブをクリックし、コンポーネントを連結するデータ フローが含まれているデータ フロー タスクをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="38c10-107">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow in which you want to connect components.</span></span>  
  
4.  <span data-ttu-id="38c10-108">**[データ フロー]** タブのデザイン画面で、連結する変換または変換元を選択します。</span><span class="sxs-lookup"><span data-stu-id="38c10-108">On the design surface of the **Data Flow** tab, select the transformation or source that you want to connect.</span></span>  
  
5.  <span data-ttu-id="38c10-109">変換または変換元の出力を表す緑の矢印を、変換または変換先にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="38c10-109">Drag the green output arrow of a transformation or a source to a transformation or to a destination.</span></span> <span data-ttu-id="38c10-110">一部のデータ フロー コンポーネントはエラー出力をとり、同様の方法で連結できます。</span><span class="sxs-lookup"><span data-stu-id="38c10-110">Some data flow components have error outputs that you can connect in the same way.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38c10-111">一部のデータ フロー コンポーネントには複数の出力があります。これらの各出力は、それぞれ個別の変換または変換先に連結できます。</span><span class="sxs-lookup"><span data-stu-id="38c10-111">Some data flow components can have multiple outputs and you can connect each output to a different transformation or destination.</span></span>  
  
6.  <span data-ttu-id="38c10-112">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38c10-112">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c10-113">参照</span><span class="sxs-lookup"><span data-stu-id="38c10-113">See Also</span></span>  
 <span data-ttu-id="38c10-114">[データフロー内のコンポーネントを追加または削除する](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="38c10-114">[Add or Delete a Component in a Data Flow](data-flow.md) </span></span>  
 <span data-ttu-id="38c10-115">[データフローコンポーネントでのエラー出力の構成](../configure-an-error-output-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="38c10-115">[Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="38c10-116">データ フロー</span><span class="sxs-lookup"><span data-stu-id="38c10-116">Data Flow</span></span>](data-flow.md)  
  
  
