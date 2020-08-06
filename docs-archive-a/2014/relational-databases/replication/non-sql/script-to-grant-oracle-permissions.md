---
title: Oracle の権限を許可するためのスクリプト | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], script to grant permissions
ms.assetid: d742fd30-347a-452f-b5fc-b03232360c6b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e25e3accd2fd73a42f27da38900cbd6d0cde6ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717912"
---
# <a name="script-to-grant-oracle-permissions"></a><span data-ttu-id="ddf4d-102">Oracle の権限を許可するためのスクリプト</span><span class="sxs-lookup"><span data-stu-id="ddf4d-102">Script to Grant Oracle Permissions</span></span>
  <span data-ttu-id="ddf4d-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレプリケーションを使用してデータをパブリッシュする Oracle データベースを構成する際には、このトピックに示すスクリプトを使用します。</span><span class="sxs-lookup"><span data-stu-id="ddf4d-103">The script provided in this topic is used during the configuration of an Oracle database that will publish data using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="ddf4d-104">このスクリプトは、インストール後に、 *\<drive>* :\\\Program Files\Microsoft SQL Server\\\ *\<InstanceName>* \MSSQL\Install\oracleadmin.sql ディレクトリで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ddf4d-104">This script is also available in the following directory after installation: *\<drive>*:\\\Program Files\Microsoft SQL Server\\*\<InstanceName>* \MSSQL\Install\oracleadmin.sql.</span></span> <span data-ttu-id="ddf4d-105">Oracle データベースの構成の詳細については、「[Oracle パブリッシャーの構成](configure-an-oracle-publisher.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddf4d-105">For more information about configuring the Oracle database, see [Configure an Oracle Publisher](configure-an-oracle-publisher.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddf4d-106">このスクリプトには、ステートメント `GRANT CREATE ANY TRIGGER TO &&AdminLogin;`が含まれています。これは、トランザクション レプリケーションで使用するトリガーで必要です。</span><span class="sxs-lookup"><span data-stu-id="ddf4d-106">This script includes the statement `GRANT CREATE ANY TRIGGER TO &&AdminLogin;`, which is required for the triggers used by transactional replication.</span></span> <span data-ttu-id="ddf4d-107">スナップショット レプリケーションしか使用しない場合は、スクリプトからこの行を削除してください。</span><span class="sxs-lookup"><span data-stu-id="ddf4d-107">If you will use only snapshot replication, remove this line from the script.</span></span>  
  
 <span data-ttu-id="ddf4d-108">**Oracle SQL\*Plus ユーティリティからスクリプトを実行するには**</span><span class="sxs-lookup"><span data-stu-id="ddf4d-108">**To run the script from the Oracle SQL\*Plus utility**</span></span>  
  
1.  <span data-ttu-id="ddf4d-109">SQL Server ディストリビューターで、コマンド プロンプト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="ddf4d-109">On the SQL Server Distributor, open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="ddf4d-110">SQL\*PLUS を使用して Oracle データベースに接続し、その既定のインストール ディレクトリから oracleadmin.sql スクリプトを実行するには、次の構文を入力します。</span><span class="sxs-lookup"><span data-stu-id="ddf4d-110">To use SQL\*PLUS to connect to the Oracle database and execute the oracleadmin.sql script from its default install directory, type the following syntax:</span></span>  
  
    ```  
    sqlplus system/P@$$W0rd@orcl @"c:\Program Files\Microsoft SQL Server\<InstanceName>\MSSQL\Install\oracleadmin.sql"  
    ```  
  
     <span data-ttu-id="ddf4d-111">この例では、ビルトイン Oracle アカウント **system** を使用して、"orcl" というネットワーク名の Oracle データベースに接続しています。</span><span class="sxs-lookup"><span data-stu-id="ddf4d-111">In this example, the built-in Oracle account **system** is used to connect to an Oracle database with a network name of "orcl".</span></span>  
  
3.  <span data-ttu-id="ddf4d-112">プロンプトが表示されたら、ユーザー名、ユーザー パスワード、および既定のテーブル スペースを指定します。</span><span class="sxs-lookup"><span data-stu-id="ddf4d-112">When prompted, specify the user name, user password, and default table space.</span></span>  
  
```  
--***********************************************************************  
-- Copyright (c) 2003 Microsoft Corporation  
--  
-- File:  
--  oracleadmin.sql  
--  
-- Purpose:  
-- PL/SQL script to create a database user with the required   
-- permissions to administer SQL Server publishing for an Oracle  
-- database.  
--  
-- &&ReplLogin        == Replication user login  
-- &&ReplPassword     == Replication user password  
-- &&DefaultTablespace == Tablespace that will serve as the default  
-- tablespace for the replication user.  
-- The replication user will be authorized to allocate UNLIMITED space  
-- on the default tablespace, which must already exist.  
--  
-- Notes:  
--  
-- This script must be run from an Oracle login having the  
-- authorization to create a new user and grant unlimited tablespace on  
-- any existing tablespace. The login must also be able to grant to the  
-- newly created login the following authorizations:  
--  
-- create public synonym  
-- drop public synonym  
-- create sequence  
--  create procedure  
-- create session  
-- create table  
-- create view  
--  
-- Additionally, the following properties are also required for  
-- transactional publications.  
--  
-- create any trigger  
--  
--  All of the privileges may be granted through a role, with the  
-- exception of create table, create view, and create any trigger.  
-- These must be granted explicitly to the replication user login.  
-- In the script, all grants are granted explicitly to the replication  
-- user.  
--  
-- In addition to these general grants, a table owner must explicitly  
-- grant select authorization to the replication user on a table before  
-- the table can be published.  
--  
***********************************************************************  
  
ACCEPT ReplLogin CHAR PROMPT 'User to create for replication: ';  
ACCEPT ReplPassword CHAR PROMPT 'Replication user passsword: ' HIDE;  
ACCEPT DefaultTableSpace CHAR DEFAULT 'SYSTEM' PROMPT 'Default tablespace: ';  
  
-- Create the replication user account  
CREATE USER &&ReplLogin IDENTIFIED BY &&ReplPassword DEFAULT TABLESPACE &&DefaultTablespace QUOTA UNLIMITED ON &&DefaultTablespace;  
  
-- It is recommended that only the required grants be granted to this  
-- user.  
--  
-- The following 5 privileges are granted explicitly, but could be  
-- granted through a role.  
GRANT CREATE PUBLIC SYNONYM TO &&ReplLogin;  
GRANT DROP PUBLIC SYNONYM TO &&ReplLogin;  
GRANT CREATE SEQUENCE TO &&ReplLogin;  
GRANT CREATE PROCEDURE TO &&ReplLogin;  
GRANT CREATE SESSION TO &&ReplLogin;  
  
-- The following privileges must be granted explicitly to the  
-- replication user.  
GRANT CREATE TABLE TO &&ReplLogin;  
GRANT CREATE VIEW TO &&ReplLogin;  
  
-- The replication user login needs to be able to create a tracking  
-- trigger on any table that is to be published in a transactional  
-- publication. The CREATE ANY privilege is used to obtain the  
-- authorization to create these triggers.  To replicate a table, the  
-- table owner must additionally explicitly grant select authorization  
-- on the table to the replication user.  
--  
-- NOTE: CREATE ANY TRIGGER is not required for snapshot publications.  
GRANT CREATE ANY TRIGGER TO &&ReplLogin;  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddf4d-113">参照</span><span class="sxs-lookup"><span data-stu-id="ddf4d-113">See Also</span></span>  
 [<span data-ttu-id="ddf4d-114">Oracle パブリッシャーの構成</span><span class="sxs-lookup"><span data-stu-id="ddf4d-114">Configure an Oracle Publisher</span></span>](configure-an-oracle-publisher.md)  
  
  
