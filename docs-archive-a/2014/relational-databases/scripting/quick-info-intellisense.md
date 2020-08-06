---
title: クイック ヒント (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Quick Info option [IntelliSense]
- declarations [IntelliSense]
- IntelliSense [SQL Server], Quick Info
- identifier declarations [IntelliSense]
ms.assetid: 3c8b59f4-1922-4bde-844f-5f2306514d96
author: rothja
ms.author: jroth
ms.openlocfilehash: 4f173c57438301702a8e51acf4531c655fde0cc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743197"
---
# <a name="quick-info-intellisense"></a><span data-ttu-id="a990d-102">クイック ヒント (IntelliSense)</span><span class="sxs-lookup"><span data-stu-id="a990d-102">Quick Info (IntelliSense)</span></span>
  <span data-ttu-id="a990d-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense による **クイック ヒント** には、コード内の識別子に関する完全な宣言が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a990d-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense **Quick Info** option displays the complete declaration for any identifier in your code.</span></span> <span data-ttu-id="a990d-104">識別子の上にマウスのポインターを置くと、黄色のポップアップ ウィンドウにその宣言が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a990d-104">When you move the mouse pointer over an identifier, its declaration is displayed in a yellow pop-up window.</span></span> <span data-ttu-id="a990d-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、データベース エンジン クエリ エディターおよび XML クエリ エディターで **クイック ヒント** を利用できます。</span><span class="sxs-lookup"><span data-stu-id="a990d-105">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **Quick Info** is available in the Database Engine and XML Query Editors.</span></span>  
  
## <a name="transact-sql-quick-info"></a><span data-ttu-id="a990d-106">Transact-SQL クイック ヒント</span><span class="sxs-lookup"><span data-stu-id="a990d-106">Transact-SQL Quick Info</span></span>  
 <span data-ttu-id="a990d-107">**クイック ヒント** には、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターに 2 種類の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a990d-107">**Quick Info** displays two types of information in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="a990d-108">デバッグ モードでない場合、 **クイック ヒント** には式の宣言が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a990d-108">When not in debug mode, **Quick Info** displays the expression declaration.</span></span> <span data-ttu-id="a990d-109">デバッグ モードの場合は、式の名前とその現在の値が **クイック ヒント** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a990d-109">When in debug mode, **Quick Info** instead displays the name of the expression and its current value.</span></span>  
  
 <span data-ttu-id="a990d-110">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターでは、 **クイック ヒント** は、IntelliSense によってサポートされる [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文の部品でのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="a990d-110">In the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, **Quick Info** is available only for those parts of the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax that IntelliSense supports.</span></span> <span data-ttu-id="a990d-111">たとえば、IntelliSense によってサポートされないデータ型を持つオブジェクトの識別子上にマウス ポインターを移動すると、そのデータ型はサポートされていない旨のメッセージが **クイック ヒント** のポップアップ ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a990d-111">For example, if you move the mouse pointer over the identifier for an object that has a data type that IntelliSense does not support, the **Quick Info** pop-up window contains a message that states that the data type is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a990d-112">参照</span><span class="sxs-lookup"><span data-stu-id="a990d-112">See Also</span></span>  
 [<span data-ttu-id="a990d-113">IntelliSense でサポートされている Transact-SQL 構文</span><span class="sxs-lookup"><span data-stu-id="a990d-113">Transact-SQL Syntax Supported by IntelliSense</span></span>](transact-sql-syntax-supported-by-intellisense.md)  
  
  
