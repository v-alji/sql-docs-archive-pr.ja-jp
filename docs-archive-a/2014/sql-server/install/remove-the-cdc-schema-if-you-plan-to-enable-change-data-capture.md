---
title: 変更データキャプチャを有効にする予定がある場合は、cdc スキーマを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: abdb33fa3d1ff022a65ed569f19d48bcf4468501
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643108"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a><span data-ttu-id="704ba-102">変更データ キャプチャを有効にする場合に cdc スキーマを削除する</span><span class="sxs-lookup"><span data-stu-id="704ba-102">Remove the cdc schema if you plan to enable change data capture</span></span>
  <span data-ttu-id="704ba-103">データベースには、既に cdc スキーマが含まれています。</span><span class="sxs-lookup"><span data-stu-id="704ba-103">A database already contains a cdc schema.</span></span> <span data-ttu-id="704ba-104">アップグレード後に変更データ キャプチャを有効にする場合は、まずこの cdc スキーマを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="704ba-104">If you plan to enable change data capture after upgrade, you must first drop this cdc schema.</span></span> <span data-ttu-id="704ba-105">データベースで変更データ キャプチャを有効にすると、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]によって、cdc という名前の新しいスキーマが作成されます。</span><span class="sxs-lookup"><span data-stu-id="704ba-105">When you enable a database for change data capture, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] will create a new schema named cdc.</span></span>  
  
  
