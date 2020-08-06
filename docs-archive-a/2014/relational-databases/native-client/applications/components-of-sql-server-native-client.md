---
title: SQL Server Native Client | のコンポーネントMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: rothja
ms.author: jroth
ms.openlocfilehash: 32438b9fb5473d9251acd0aceddb46db373f3548
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642041"
---
# <a name="components-of-sql-server-native-client"></a><span data-ttu-id="2ea67-102">SQL Server Native Client のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="2ea67-102">Components of SQL Server Native Client</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="2ea67-103">Native Client には、次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ea67-103">Native Client contains the following components:</span></span>  
  
|<span data-ttu-id="2ea67-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2ea67-104">Component</span></span>|<span data-ttu-id="2ea67-105">説明</span><span class="sxs-lookup"><span data-stu-id="2ea67-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ea67-106">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="2ea67-106">sqlncli11.dll</span></span>|<span data-ttu-id="2ea67-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client のすべての機能を含む DLL (ダイナミック リンク ライブラリ) ファイル。</span><span class="sxs-lookup"><span data-stu-id="2ea67-107">The dynamic-link library (DLL) file that contains all of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client functionality.</span></span> <span data-ttu-id="2ea67-108">このファイルには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2ea67-108">This includes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>|  
|<span data-ttu-id="2ea67-109">sqlnclir11.rll</span><span class="sxs-lookup"><span data-stu-id="2ea67-109">sqlnclir11.rll</span></span>|<span data-ttu-id="2ea67-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ライブラリに付随するリソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="2ea67-110">The accompanying resource file for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client library.</span></span>|  
|<span data-ttu-id="2ea67-111">s10ch_sqlncli.chm</span><span class="sxs-lookup"><span data-stu-id="2ea67-111">s10ch_sqlncli.chm</span></span>|<span data-ttu-id="2ea67-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーまたは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ ソースを作成する方法について記載している、データ ソース ウィザードのヘルプ ファイル。</span><span class="sxs-lookup"><span data-stu-id="2ea67-112">The Data Source Wizard help file that documents how to create a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data source using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>|  
|<span data-ttu-id="2ea67-113">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="2ea67-113">sqlncli.h</span></span>|<span data-ttu-id="2ea67-114">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用する場合に必要となる、新しいすべての定義を含む [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイル。</span><span class="sxs-lookup"><span data-stu-id="2ea67-114">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header file that contains all of the new definitions needed in order to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="2ea67-115">このヘッダー ファイルは、odbcss.h ヘッダー ファイルと sqloledb.h ヘッダー ファイルの両方に置き換わるものです。</span><span class="sxs-lookup"><span data-stu-id="2ea67-115">This header file replaces both the odbcss.h and the sqloledb.h header files.</span></span> <span data-ttu-id="2ea67-116">**注:** 同じプログラムで sqlncli と odbcss.h を参照することはできませんが、最初に sqloledb が定義されていれば、同じプログラムで sqlncli と sqloledb を参照できます。</span><span class="sxs-lookup"><span data-stu-id="2ea67-116">**Note:**  You cannot reference sqlncli.h and odbcss.h in the same program, but you can reference sqlncli.h and sqloledb.h in same program as long as sqloledb.h is defined first.</span></span>|  
|<span data-ttu-id="2ea67-117">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="2ea67-117">sqlncli11.lib</span></span>|<span data-ttu-id="2ea67-118">Native Client ODBC ドライバーの一部である**bcp**ユーティリティ関数を直接呼び出すために必要なライブラリファイル [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2ea67-118">The library file needed to directly call the **bcp** utility functions that are part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="2ea67-119">**注:** プログラミングコードで sqlncli11 ファイルを参照する場合は、sqlncli11.dll ファイルがシステムパスと、アプリケーションを使用するユーザーのシステムパスに存在することを確認する必要がありますが、</span><span class="sxs-lookup"><span data-stu-id="2ea67-119">**Note:**  If you do reference the sqlncli11.lib file in your programming code, you need to make sure that the sqlncli11.dll file is in your system path, and in the system path of the users that make use of your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ea67-120">参照</span><span class="sxs-lookup"><span data-stu-id="2ea67-120">See Also</span></span>  
 [<span data-ttu-id="2ea67-121">SQL Server Native Client を使用したアプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="2ea67-121">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
