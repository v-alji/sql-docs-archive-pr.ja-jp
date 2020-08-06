---
title: データ処理拡張機能の削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9f5dfd3a6a7615fa3fd91c917bba6dbf0808f0f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741585"
---
# <a name="removing-a-data-processing-extension"></a><span data-ttu-id="3c9b4-102">データ処理拡張機能の削除</span><span class="sxs-lookup"><span data-stu-id="3c9b4-102">Removing a Data Processing Extension</span></span>
  <span data-ttu-id="3c9b4-103">データ処理拡張機能を削除する場合は、データ処理拡張機能の **Extension** 要素を構成ファイルから削除するだけです。</span><span class="sxs-lookup"><span data-stu-id="3c9b4-103">To remove a data processing extension, simply remove the **Extension** element for your data processing extension from the configuration file.</span></span> <span data-ttu-id="3c9b4-104">レポート サーバーに加えてレポート デザイナーにもエントリを作成した場合は、RSReportServer.config ファイルと RSReportDesigner.config ファイルの両方から **Extension** 要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="3c9b4-104">If you made entries for a report server as well as Report Designer, remove the **Extension** element from both the RSReportServer.config and RSReportDesigner.config files.</span></span> <span data-ttu-id="3c9b4-105">構成情報を削除すると、そのコンポーネントではデータ処理拡張機能を使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3c9b4-105">After the configuration information is removed, the data processing extension is no longer available to the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9b4-106">参照</span><span class="sxs-lookup"><span data-stu-id="3c9b4-106">See Also</span></span>  
 <span data-ttu-id="3c9b4-107">[Reporting Services 拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="3c9b4-107">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="3c9b4-108">[データ処理拡張機能の実装](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="3c9b4-108">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="3c9b4-109">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="3c9b4-109">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
