---
title: データソースの追加 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: b4ac6f0e-8e6a-4b1a-9a7e-60e0a69b2180
author: rothja
ms.author: jroth
ms.openlocfilehash: 519990e9dd9d84f75c4efc6c76b910f0a359f52f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634503"
---
# <a name="add-a-data-source-odbc"></a><span data-ttu-id="fc103-102">データ ソースの追加 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="fc103-102">Add a Data Source (ODBC)</span></span>
  <span data-ttu-id="fc103-103">データソースを追加するには、ODBC アドミニストレーターを使用するか、プログラムで ( [Sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)を使用)、またはファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fc103-103">You can add a data source by using ODBC Administrator, programmatically (by using [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)), or by creating a file.</span></span>  
  
### <a name="to-add-a-data-source-by-using-odbc-administrator"></a><span data-ttu-id="fc103-104">ODBC アドミニストレーターを使用してデータ ソースを追加するには</span><span class="sxs-lookup"><span data-stu-id="fc103-104">To add a data source by using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="fc103-105">**コントロールパネル**で、[**管理ツール**]、[**データソース (ODBC)**] の順にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="fc103-105">From the **Control Panel**, access **Administrative Tools** and then **Data Sources (ODBC)**.</span></span> <span data-ttu-id="fc103-106">または、odbcad32.exe を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="fc103-106">Alternatively, you can invoke odbcad32.exe.</span></span>  
  
2.  <span data-ttu-id="fc103-107">[**ユーザー dsn**]、 **[システム dsn**]、または [**ファイル dsn** ] タブをクリックし、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fc103-107">Click the **User DSN**, **System DSN**, or **File DSN** tab, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="fc103-108">[ **SQL Server**] をクリックし、[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fc103-108">Click **SQL Server**, and then click **Finish**.</span></span>  
  
4.  <span data-ttu-id="fc103-109">SQL Server への新しいデータ ソースの作成ウィザードの手順に従って実行します。</span><span class="sxs-lookup"><span data-stu-id="fc103-109">Complete the Steps in the Create a New Data Source to SQL Server Wizard.</span></span>  
  
### <a name="to-add-a-data-source-programmatically"></a><span data-ttu-id="fc103-110">データ ソースをプログラムで追加するには</span><span class="sxs-lookup"><span data-stu-id="fc103-110">To add a data source programmatically</span></span>  
  
1.  <span data-ttu-id="fc103-111">2番目のパラメーターを ODBC_ADD_DSN または ODBC_ADD_SYS_DSN に設定して[Sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fc103-111">Call [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) with the second parameter set to either ODBC_ADD_DSN or ODBC_ADD_SYS_DSN.</span></span>  
  
### <a name="to-add-a-file-data-source"></a><span data-ttu-id="fc103-112">ファイル データ ソースを追加するには</span><span class="sxs-lookup"><span data-stu-id="fc103-112">To add a file data source</span></span>  
  
1.  <span data-ttu-id="fc103-113">接続文字列で SAVEFILE = file_name パラメーターを指定して[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fc103-113">Call [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) with a SAVEFILE=file_name parameter in the connect string.</span></span> <span data-ttu-id="fc103-114">接続が確立されると、ODBC ドライバーによって、SAVEFILE パラメーターが指す場所の接続パラメーターを使用してファイル データ ソースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fc103-114">If the connect is successful, the ODBC driver creates a file data source with the connection parameters in the location pointed to by the SAVEFILE parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc103-115">参照</span><span class="sxs-lookup"><span data-stu-id="fc103-115">See Also</span></span>  
 [<span data-ttu-id="fc103-116">SQL Server ODBC ドライバーを構成する方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="fc103-116">Configuring the SQL Server ODBC Driver How-to Topics</span></span>](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
