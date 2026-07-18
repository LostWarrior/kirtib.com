---
author: "Kirti Bhardwaj"
date: 2023-11-25
linktitle: unique-emails
prev: /posts/median-sorted-array
title: Unique Email Addresses
weight: 10
draft: false
---

### Problem Statement
Every email consists of a local name and a domain name, separated by the @ sign.

For example, in alice@leetcode.com, alice is the local name, and leetcode.com is the domain name.

Besides lowercase letters, these emails may contain '.'s or '+'s.

If you add periods ('.') between some characters in the local name part of an email address, mail sent there will be forwarded to the same address without dots in the local name.  For example, "alice.z@leetcode.com" and "alicez@leetcode.com" forward to the same email address.  (Note that this rule does not apply for domain names.)

If you add a plus ('+') in the local name, everything after the first plus sign will be ignored. This allows certain emails to be filtered, for example m.y+name@email.com will be forwarded to my@email.com.  (Again, this rule does not apply for domain names.)

It is possible to use both of these rules at the same time.

Given a list of emails, we send one email to each address in the list.  How many different addresses actually receive mails? 

Here is the link to the problem [leetcode](https://leetcode.com/problems/unique-email-addresses/)

### Example

    Input: ["test.email+alex@leetcode.com","test.e.mail+bob.cathy@leetcode.com","testemail+david@lee.tcode.com"]
    Output: 2
    Explanation: "testemail@leetcode.com" and "testemail@lee.tcode.com" actually receive mails

### Discussion


This is an easy problem to solve. First we divide the address into local and domain parts by splitting it on "@". Now, for local part we split it on "." and join all the parts back together thus, converting abc.def => abcdef and thanks to chaining in js we split the result again on "+" and assign everything before the "+" character to local variable.

From here on it is a simple task of creating the final string and adding it to the accumulator provided.

### Solution
    /**
    * @param {string[]} emails
    * @return {number}
    */
    var numUniqueEmails = function(emails) {
        let finalEmails = emails.reduce((acc,email) => {
            let arr = email.split("@");
            let local = arr[0].split(".").join("").split("+")[0];
            let domain = arr[1];
            
            let addr = `${local}@${domain}`;
            
            acc.add(addr);
            return acc;
        },new Set());
        
        return finalEmails.size;
    };