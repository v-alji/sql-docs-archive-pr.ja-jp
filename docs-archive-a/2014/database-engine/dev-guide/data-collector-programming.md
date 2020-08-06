---
title: データコレクターのプログラミング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- data collector [SQL Server], programming
ms.assetid: 53b4752b-055d-4716-b2bc-75b4cce84101
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9f4da839f25da8f8aab3e21fa98547eff72d2140
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742541"
---
# <a name="data-collector-programming"></a><span data-ttu-id="b14d0-102">データ コレクターのプログラミング</span><span class="sxs-lookup"><span data-stu-id="b14d0-102">Data Collector Programming</span></span>
  <span data-ttu-id="b14d0-103"><xref:Microsoft.SqlServer.Management.Collector> のデータ コレクター API を使用すると、オブジェクト モデルを通じてすべての構成操作をプログラムで制御できます。</span><span class="sxs-lookup"><span data-stu-id="b14d0-103">The data collector API, in <xref:Microsoft.SqlServer.Management.Collector>, allows programmatic control of all configuration operations through the object model.</span></span> <span data-ttu-id="b14d0-104">また、API を使用するデータ収集操作の多くは、サーバーにインストールされているストアド プロシージャとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="b14d0-104">In addition, many of the data collection operations that use the API are implemented as stored procedures that are installed on the server.</span></span>

 <span data-ttu-id="b14d0-105">次の図では、データ コレクター オブジェクト モデルの主要な要素を示します。</span><span class="sxs-lookup"><span data-stu-id="b14d0-105">The following illustration shows key elements of the data collector object model.</span></span>

 <span data-ttu-id="b14d0-106">![データ コレクター オブジェクト モデル](../../../2014/database-engine/dev-guide/media/dc-objectmodel.gif "データ コレクター オブジェクト モデル")</span><span class="sxs-lookup"><span data-stu-id="b14d0-106">![The Data Collector Object Model](../../../2014/database-engine/dev-guide/media/dc-objectmodel.gif "The Data Collector Object Model")</span></span>


