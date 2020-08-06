---
title: 配信拡張機能の削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c4320f46b5013b0fa2accbc81792748c2d9f384
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646044"
---
# <a name="removing-a-delivery-extension"></a><span data-ttu-id="761cf-102">配信拡張機能の削除</span><span class="sxs-lookup"><span data-stu-id="761cf-102">Removing a Delivery Extension</span></span>
  <span data-ttu-id="761cf-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を削除する場合は、配信拡張機能の **Extension** 要素を構成ファイルから削除するだけです。</span><span class="sxs-lookup"><span data-stu-id="761cf-103">To remove a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, simply remove the **Extension** element for your delivery extension from the configuration file.</span></span> <span data-ttu-id="761cf-104">構成情報を削除した後は、配信拡張機能をレポート サーバーに使用できません。</span><span class="sxs-lookup"><span data-stu-id="761cf-104">After the configuration information is removed, the delivery extension is no longer available to the report server.</span></span>  
  
 <span data-ttu-id="761cf-105">配信拡張機能の対応する **Extension** 要素を構成ファイルから削除すると、この要素はレポート サーバーに登録されなくなります。</span><span class="sxs-lookup"><span data-stu-id="761cf-105">Once a delivery extension's corresponding **Extension** element is removed from the configuration file, it is no longer registered with the report server.</span></span> <span data-ttu-id="761cf-106">レポート サーバーは、配信拡張機能の一覧からエントリを削除し、配信拡張機能を使用するサブスクリプションをすべて非アクティブにします。</span><span class="sxs-lookup"><span data-stu-id="761cf-106">The report server removes the entry from the list of delivery extensions and deactivates any subscriptions which use that delivery extension.</span></span> <span data-ttu-id="761cf-107">配信拡張機能が削除されていると、ユーザーは配信拡張機能を通知のメソッドとして選択できなくなります。</span><span class="sxs-lookup"><span data-stu-id="761cf-107">When a delivery extension is removed, users are no longer able to select it as a method of notification.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761cf-108">参照</span><span class="sxs-lookup"><span data-stu-id="761cf-108">See Also</span></span>  
 <span data-ttu-id="761cf-109">[配信拡張機能の実装](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="761cf-109">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="761cf-110">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="761cf-110">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
