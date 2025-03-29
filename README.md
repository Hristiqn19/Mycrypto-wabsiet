# Mycrypto-wabsiet<!DOCTYPE html><html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MyCryptoToken</title>
    <script src="https://cdn.jsdelivr.net/npm/web3/dist/web3.min.js"></script>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        button { padding: 10px; margin: 5px; }
    </style>
</head>
<body>
    <h1>MyCryptoToken (MCT)</h1>
    <button onclick="connectWallet()">Свържи MetaMask</button>
    <p id="account"></p>
    <button onclick="getBalance()">Провери Баланс</button>
    <p id="balance"></p><script>
    let account;
    const contractAddress = "0xYourContractAddress"; // Смени с реалния адрес
    const contractABI = [ /* Добави ABI тук */ ];
    
    async function connectWallet() {
        if (window.ethereum) {
            const accounts = await ethereum.request({ method: "eth_requestAccounts" });
            account = accounts[0];
            document.getElementById("account").innerText = "Свързан: " + account;
        } else {
            alert("Инсталирай MetaMask!");
        }
    }
    
    async function getBalance() {
        const web3 = new Web3(window.ethereum);
        const contract = new web3.eth.Contract(contractABI, contractAddress);
        const balance = await contract.methods.balanceOf(account).call();
        document.getElementById("balance").innerText = "Баланс: " + balance;
    }
</script>

</body>
</html>
