---
title: 開発、テスト、および実稼働データベース (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- production databases [SQL Server]
- testing databases
- database testing [SQL Server]
ms.assetid: cb403330-8cbe-41c6-bd23-bc432d50f173
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98ac88aec42b53012e0f57233a089bddbd3c8cae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713686"
---
# <a name="development-test-and-production-databases-visual-database-tools"></a><span data-ttu-id="8d894-102">開発用データベース、テスト用データベース、および実行時用データベース (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8d894-102">Development, Test, and Production Databases (Visual Database Tools)</span></span>
  <span data-ttu-id="8d894-103">まったく同じ構成のデータベースが 2 つある場合は、一方のデータベースで変更を行い、その変更をもう一方のデータベースに反映させることができます。</span><span class="sxs-lookup"><span data-stu-id="8d894-103">If you have two databases with identical structure, you can make changes in one database and propagate those changes to the other.</span></span> <span data-ttu-id="8d894-104">たとえば、個人で使用する開発用データベースとグループ全体で使用するテスト用データベースがある場合は、開発用データベースを変更してから、その変更をテスト用データベースに反映させます。</span><span class="sxs-lookup"><span data-stu-id="8d894-104">For example, if you have a personal development database and a group-wide test database, you can modify the development database, then propagate those changes to the test database.</span></span>  
  
 <span data-ttu-id="8d894-105">これを実現するには、すべての変更を開発用データベースでの単一のセッション内で実行し、セッションの変更スクリプトを作成して、そのスクリプトを後からテスト用データベースで実行します。</span><span class="sxs-lookup"><span data-stu-id="8d894-105">To accomplish this, perform all the modifications in a single session with the development database, create a Change Script of your session and later run the script on the test database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d894-106">参照</span><span class="sxs-lookup"><span data-stu-id="8d894-106">See Also</span></span>  
 [<span data-ttu-id="8d894-107">マルチユーザー環境 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="8d894-107">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
