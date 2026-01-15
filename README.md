# Mochimo Old Wallets (CLI, Java)
This archive contains three command-line wallet binaries for the Mochimo cryptocurrency, preserved for historical purposes, and for potential use in recovering Mochimo cryptocurrency Command Line wallets that were created between the network launch date of Mochimo on June 25, 2018 and the final release of the CLI wallet tool.

## Requirements
These wallets should work on most 32-bit+ Linux systems, but are tested to work on all releases of Ubuntu 64-bit between 16.04 and 24.04 LTS. 

## Usage
```
Usage: wallet-06252018 [-option -option2 . . .] [wallet_file]
options:
           -cFNAME  set alternate IP list to FNAME
           -aS      set address string to S
           -pN      set TCP port to N
           -v       verbose output
           -n       create new wallet
```

If you are trying to invoke the wallet, you may simply pass it the wallet file name you are trying to open with no optional flags.  You will need your original wallet password to open the file.  Depending on your system, you may have to set the wallet binary as executable with:
```
chmod +x [FILENAME]
```
## Password Recovery (Probably Not Possible)
There is no currently-known way to recover wallet file passwords as of early 2026, though there are theoretical potential brute-force methods if you happen to recall your exact wallet balance, or the plain-text name of one of the accounts you had stored in it.

## Account Recovery Path
### Disclaimer: Proceed at your own risk.  This is a community supplied set of instructions that may or may not work for you, and may result in the loss of your funds.  No warranty is provided, and following these instructions means you understand the risk, and accept responsibility for the outcome.  If you are not prepared to accept that risk, do not follow the below steps.  Take note that if this process completes successfully you will have an unencrypted file on your disk that contains your legacy Mochimo address and secret key.  Take care that no one may access this file or you may lose your funds.

1. Always make copies of your old wallet file before you begin, and preserve the original file untouched.  
2. Try to load THE COPY using all three wallet binaries starting with the most recent (wallet-101921), as there were three different wallet formats in the early days of the project.  If a wallet binary is not compatible with your wallet file it will error out on attempting to load the file.
3. Depending on the version, you may have to CTRL+C to interrupt the wallet's attempt to access the old V1 network (which no longer exists).
4. Once the file is open, you will be able to view your account balances, and importantly their index numbers.  Note that the balance will be whatever value the wallet file last saw the last time the live network was connected to, and may not reflect the actual balance of the associated account.
5. Navigate to the export address option, which depending on the version of your wallet may be on either the first or second menu.  
6. You will be asked to select the index number of the account you want to export.  Just enter the number.  If prompted, select yes to include the balance and yes to include the secret.
7. Name the export file something like account-name-legacy.mcm.  When you look at that file on disk it should either be 2240 bytes, or 2248 bytes, depending on the wallet version.
8. Secure this legacy MCM adddress file.  It has an unencrypted copy of your address and secret key in it.  Anyone who has access to this file can potentially access your funds.

## Further Steps Are Required

The next steps in the recovery process are to either manually condition that unencrypted datafile to be importable via the Chromium Extension wallet (hard, requires a hex editor/expertise) or use the old Mojo Java wallet to import the legacy MCM address file.  The .jar file for the Mojo wallet is present in the repository as well.  Mojo likewise cannot connect to the v3 network, but you can still use it to create a new, empty wallet, and import a legacy key pair (though Mojo won't show you any balance).  Once you've done that you can save and exit the Mojo wallet file, then import the Mojo Java wallet file into the Chromium Extension wallet (still hard, but slightly less).  For that approach, you need to install java and then open the Mojo jar file.  Once the Mojo wallet is imported into the Chromium extension you should see your coin balance.  It is suggested that you **Immediately transfer 100% of those coins** to your Account 1 in Chromium if you want the funds to be protected and recoverable via the seed phrase you got when you created your browser extension wallet.  Again, this is at your own risk.
