---
title: 高速解析の設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6ff2c6ecd536dd5ecc34dceb358ffcf578ff3a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631153"
---
# <a name="set-fast-parse"></a><span data-ttu-id="84696-102">高速解析を設定する</span><span class="sxs-lookup"><span data-stu-id="84696-102">Set Fast Parse</span></span>
  <span data-ttu-id="84696-103">高速解析を使用するフラット ファイル ソースまたはデータ変換の変換の列ごとに、高速解析プロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84696-103">The fast parse property must be set for each column of the source or transformation that uses fast parse.</span></span> <span data-ttu-id="84696-104">プロパティを設定するには、フラット ファイル ソースおよびデータ変換の変換の詳細エディターを使用します。</span><span class="sxs-lookup"><span data-stu-id="84696-104">To set the property, use the Advanced editor of the Flat File source and Data Conversion transformation.</span></span>  
  
### <a name="to-set-fast-parse"></a><span data-ttu-id="84696-105">高速解析を設定するには</span><span class="sxs-lookup"><span data-stu-id="84696-105">To set fast parse</span></span>  
  
1.  <span data-ttu-id="84696-106">フラット ファイル ソースまたはデータ変換の変換を右クリックし、 **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84696-106">Right-click the Flat File source or Data Conversion transformation, and then click **Show Advanced Editor**.</span></span>  
  
2.  <span data-ttu-id="84696-107">**[詳細エディター]** ダイアログ ボックスの **[入力プロパティと出力プロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="84696-107">In the **Advanced Editor** dialog box, click the **Input and Output Properties** tab.</span></span>  
  
3.  <span data-ttu-id="84696-108">**[入力および出力]** ペインで、高速解析を有効にする列をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84696-108">In the **Inputs and Outputs** pane, click the column for which you want to enable fast parse.</span></span>  
  
4.  <span data-ttu-id="84696-109">プロパティウィンドウで、[**カスタムプロパティ**] ノードを展開し、 `FastParse` プロパティをに設定し `True` ます。</span><span class="sxs-lookup"><span data-stu-id="84696-109">In the Properties window, expand the **Custom Properties** node, and then set the `FastParse` property to `True`.</span></span>  
  
5.  <span data-ttu-id="84696-110">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84696-110">Click **OK**.</span></span>  
  
  
