---
layout: post
title: Inventory transactions logging (InventSumLogTTS) optimization
---

Inventory transactions logging (InventSumLogTTS) is not turned on for all items and the old records in the log are automatically removed.

Changes will be made to prevent records from being inserted into the **Inventory transactions** log table (InventSumLogTTS) in certain conditions. This prevents the table from getting too large and causing performance issues.

When planning processes are enabled in a company, which means that **Master planning > Setup > Master planning parameters > Disable all planning processes** is set to **No**, inventory transactions logging (InventSumLogTTS) is not turned on in the following cases:

- The warehouse on the transaction has the **Manual replenishment** setup.
- The coverage code for the item and its product dimensions is **Manual.**
- The transaction is related to **Blocking inventory statuses.**
- The item is disabled for planning via the **Product lifecycle state** parameter on the item master.

When planning processes are disabled in a company, which means that **Master planning > Setup > Master planning parameters > Disable all planning processes** is set to **Yes**, inventory transactions logging is never turned on.

The **Inventory transactions log** table will be periodically cleaned up to remove all records that are older than 90 days. The cleanup is triggered automatically by regenerating the master plan.

[Source](https://roadmap.dynamics.com)
