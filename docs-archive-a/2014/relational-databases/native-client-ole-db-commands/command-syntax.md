---
title: コマンド構文 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
author: rothja
ms.author: jroth
ms.openlocfilehash: da5ddb75a5c6fc10db031707b7d97ead71363e9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741909"
---
# <a name="command-syntax"></a><span data-ttu-id="a48a8-102">コマンドの構文</span><span class="sxs-lookup"><span data-stu-id="a48a8-102">Command Syntax</span></span>
  <span data-ttu-id="a48a8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、DBGUID_SQL マクロで指定されたコマンド構文を認識します。</span><span class="sxs-lookup"><span data-stu-id="a48a8-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes command syntax specified by the DBGUID_SQL macro.</span></span> <span data-ttu-id="a48a8-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの場合、指定子は、ODBC SQL、ISO、およびの混在が有効な構文であることを示し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a48a8-104">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the specifier indicates that an amalgam of ODBC SQL, ISO, and [!INCLUDE[tsql](../../includes/tsql-md.md)] is valid syntax.</span></span> <span data-ttu-id="a48a8-105">たとえば、次の SQL ステートメントでは、ODBC SQL のエスケープ シーケンスを使用して、LCASE 文字列関数を指定しています。</span><span class="sxs-lookup"><span data-stu-id="a48a8-105">For example, the following SQL statement uses an ODBC SQL escape sequence to specify the LCASE string function:</span></span>  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 <span data-ttu-id="a48a8-106">LCASE 関数は、大文字をすべて小文字に変換した文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="a48a8-106">LCASE returns a character string, converting all uppercase characters to their lowercase equivalents.</span></span> <span data-ttu-id="a48a8-107">ISO の文字列関数 LOWER も同じ操作を実行します。つまり、次の SQL ステートメントは、上記の ODBC ステートメントと同義の ISO ステートメントになります。</span><span class="sxs-lookup"><span data-stu-id="a48a8-107">The ISO string function LOWER performs the same operation, so the following SQL statement is a ISO equivalent to the ODBC statement presented above:</span></span>  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 <span data-ttu-id="a48a8-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、コマンドのテキストとして指定した場合に、ステートメントのいずれかの形式を正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="a48a8-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider processes either form of the statement successfully when specified as text for a command.</span></span>  
  
## <a name="stored-procedures"></a><span data-ttu-id="a48a8-109">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a48a8-109">Stored Procedures</span></span>  
 <span data-ttu-id="a48a8-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB provider コマンドを使用してストアドプロシージャを実行する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンドテキストで ODBC CALL エスケープシーケンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a48a8-110">When executing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider command, use the ODBC CALL escape sequence in the command text.</span></span> <span data-ttu-id="a48a8-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次に、Native Client OLE DB プロバイダーは、のリモートプロシージャコール機構を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コマンド処理を最適化します。</span><span class="sxs-lookup"><span data-stu-id="a48a8-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider then uses the remote procedure call mechanism of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to optimize command processing.</span></span> <span data-ttu-id="a48a8-112">たとえば次のような場合、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント形式ではなく、ODBC SQL ステートメントをコマンド テキストとして使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a48a8-112">For example, the following ODBC SQL statement is preferred command text over the [!INCLUDE[tsql](../../includes/tsql-md.md)] form:</span></span>  
  
-   <span data-ttu-id="a48a8-113">ODBC SQL</span><span class="sxs-lookup"><span data-stu-id="a48a8-113">ODBC SQL</span></span>  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   <span data-ttu-id="a48a8-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a48a8-114">Transact-SQL</span></span>  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a48a8-115">参照</span><span class="sxs-lookup"><span data-stu-id="a48a8-115">See Also</span></span>  
 [<span data-ttu-id="a48a8-116">コマンド</span><span class="sxs-lookup"><span data-stu-id="a48a8-116">Commands</span></span>](commands.md)  
  
  
