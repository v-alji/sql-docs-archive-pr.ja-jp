---
title: データソースの削除 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e8acd6414b39b317ff0fcfe1b7b9fbab38ae0a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634501"
---
# <a name="delete-a-data-source-odbc"></a><span data-ttu-id="0afba-102">データ ソースの削除 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="0afba-102">Delete a Data Source (ODBC)</span></span>
  <span data-ttu-id="0afba-103">データソースを削除するには、ODBC 管理者を使用してプログラムで ( [Sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)を使用)、またはファイルを削除します (ファイルデータソース名が指定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="0afba-103">You can delete a data source by using ODBC Administrator, programmatically (by using [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), or by deleting a file (if a file data source name).</span></span>  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a><span data-ttu-id="0afba-104">ODBC アドミニストレーターを使用してデータ ソースを削除するには</span><span class="sxs-lookup"><span data-stu-id="0afba-104">To delete a data source by using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="0afba-105">**コントロールパネル**で、[**管理ツール**] を開き、[**データソース (ODBC)**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0afba-105">In **Control Panel**, open **Administrative Tools**, and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="0afba-106">コマンド プロンプトから odbcad32.exe を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="0afba-106">Alternatively, you can run odbcad32.exe from the command prompt.</span></span>  
  
2.  <span data-ttu-id="0afba-107">[**ユーザー dsn**]、[**システム dsn**]、または [**ファイル dsn** ] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0afba-107">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="0afba-108">削除するデータ ソースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0afba-108">Click the data source to delete.</span></span>  
  
4.  <span data-ttu-id="0afba-109">[**削除**] をクリックし、削除を確定します。</span><span class="sxs-lookup"><span data-stu-id="0afba-109">Click **Remove**, and then confirm the deletion.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0afba-110">例</span><span class="sxs-lookup"><span data-stu-id="0afba-110">Example</span></span>  
 <span data-ttu-id="0afba-111">プログラムによってデータソースを削除するには、2番目のパラメーターとして ODBC_REMOVE_DSN または ODBC_REMOVE_SYS_DSN を使用して[Sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0afba-111">To programmatically delete a data source, call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) using either ODBC_REMOVE_DSN or ODBC_REMOVE_SYS_DSN as the second parameter.</span></span>  
  
 <span data-ttu-id="0afba-112">次のサンプルでは、データ ソースをプログラムで削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0afba-112">The following sample shows how you can programmatically delete a data source.</span></span>  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0afba-113">参照</span><span class="sxs-lookup"><span data-stu-id="0afba-113">See Also</span></span>  
 [<span data-ttu-id="0afba-114">SQL Server ODBC ドライバーを構成する方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="0afba-114">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
