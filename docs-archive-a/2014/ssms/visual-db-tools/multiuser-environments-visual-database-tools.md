---
title: マルチユーザー環境 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- users [SQL Server], multiuser environments
- conflict resolution [Visual Database Tools]
- multiple users making database changes
- multiuser environments [Visual Database Tools]
- database modifications [SQL Server]
- version control [Visual Database Tools]
- Visual Database Tools [SQL Server], multiuser environments
ms.assetid: 330bd48c-9427-4967-b58e-b7c492d5ee36
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2e219ecda25f477aa459de674a43d9c2360376ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634201"
---
# <a name="multiuser-environments-visual-database-tools"></a><span data-ttu-id="5fb24-102">マルチユーザー環境 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5fb24-102">Multiuser Environments (Visual Database Tools)</span></span>
  <span data-ttu-id="5fb24-103">マルチユーザー環境とは、複数のユーザーが同じデータベースに同時に接続し、変更を行うことができる環境です。</span><span class="sxs-lookup"><span data-stu-id="5fb24-103">A multiuser environment is one in which other users can connect and make changes to the same database that you are working with.</span></span> <span data-ttu-id="5fb24-104">その結果、複数のユーザーが同時に同じデータベース オブジェクトに対する作業を行う場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fb24-104">As a result, several users might be working with the same database objects at the same time.</span></span> <span data-ttu-id="5fb24-105">したがって、マルチユーザー環境では、あるユーザーが使用しているデータベースが、自身が変更を行っている最中に他のユーザーが行った変更による影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5fb24-105">Thus, a multiuser environment introduces the possibility of the database being affected by changes made by other users while you are making changes, and vice versa.</span></span>  
  
 <span data-ttu-id="5fb24-106">マルチユーザー環境のデータベースで作業するときの重要な問題はアクセス許可です。</span><span class="sxs-lookup"><span data-stu-id="5fb24-106">A key issue when working with databases in a multiuser environment is access permissions.</span></span> <span data-ttu-id="5fb24-107">データベースに対してユーザーが持っているアクセス許可により、ユーザーがそのデータベースについて行うことができる作業の範囲が決まります。</span><span class="sxs-lookup"><span data-stu-id="5fb24-107">The permissions you have for the database determine the extent of the work you can do with the database.</span></span> <span data-ttu-id="5fb24-108">たとえば、データベースのオブジェクトを変更するには、データベースに対する適切な書き込みアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="5fb24-108">For example, to make changes to objects in a database, you must have the appropriate write permissions for the database.</span></span> <span data-ttu-id="5fb24-109">データベースでのアクセス許可の詳細については、使用しているデータベースのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fb24-109">For more information about permissions in your database, see your database documentation.</span></span> <span data-ttu-id="5fb24-110">詳しくは、「[アクセス許可と Visual Database Tools (Visual Database Tools)](visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5fb24-110">For more information see [Permissions and Visual Database Tools &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="5fb24-111">テーブルに行った変更を保存する際に、そのユーザーが最後にテーブルへの変更を保存してからデータベースが変更されていないかどうか、テーブル デザイナーによって確認が行われます。</span><span class="sxs-lookup"><span data-stu-id="5fb24-111">When you save changes made to tables, Table Designer verifies that the database has not been modified since you last saved changes.</span></span> <span data-ttu-id="5fb24-112">他のユーザーが変更を行っていた場合は、データベースが変更されていることが通知されます。</span><span class="sxs-lookup"><span data-stu-id="5fb24-112">If another user has made changes, you will be notified that the database has been modified.</span></span> <span data-ttu-id="5fb24-113">これらの変更は調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fb24-113">You may need to reconcile these changes.</span></span> <span data-ttu-id="5fb24-114">詳しくは、「[複数のユーザーによる変更の調整 (Visual Database Tools)](reconcile-changes-made-by-multiple-users-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5fb24-114">For more information, see [Reconcile Changes Made by Multiple Users &#40;Visual Database Tools&#41;](reconcile-changes-made-by-multiple-users-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="5fb24-115">マルチユーザー環境では、競合する変更を避けるために特に注意が必要なことがあります。</span><span class="sxs-lookup"><span data-stu-id="5fb24-115">In a multiuser environment there are special considerations to keep in mind to avoid conflicting changes.</span></span> <span data-ttu-id="5fb24-116">詳しくは、「[運用されているデータベースを変更するときの問題 (Visual Database Tools)](issues-of-database-evolution-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5fb24-116">For more information, see [Issues of Database Evolution &#40;Visual Database Tools&#41;](issues-of-database-evolution-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="5fb24-117">問題を回避する方法の 1 つは、変更を行う場合に、テスト データベースなどのデータベースのコピーを使用することです。さらに変更点を元のデータベースに反映する変更スクリプトを作成し、オフラインで競合の問題を解消した後で、実行します。</span><span class="sxs-lookup"><span data-stu-id="5fb24-117">One way to avoid problems is to work in a copy of the database, such as a test database, when you make changes, then you can create a change script that you can run to make those changes on the original database after resolving conflicts offline.</span></span> <span data-ttu-id="5fb24-118">詳しくは、「[開発用データベース、テスト用データベース、および実行時用データベース (Visual Database Tools)](development-test-and-production-databases-visual-database-tools.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5fb24-118">For more information see [Development, Test, and Production Databases &#40;Visual Database Tools&#41;](development-test-and-production-databases-visual-database-tools.md).</span></span>  
  
  
