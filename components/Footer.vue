<template>
    <nav class="footer-container">
        <img class="linea-fina"  src="/public/Line 6.png">
        <div class="footer">
            <div class="img-footer">
                <img src="/public/logo.png">
            </div>

            <div class="info-footer">
                <div class="top">
                    <p>About</p>
                    <p>SteamWorks</p>
                    <p>Support</p>
                </div>
                <div class="bottom">
                    <p>CONTACT US</p>
                    <p>Legal Info</p>
                    <p>Cookies</p>
                </div>
            </div>

            <div class="left-footer">
                <div class="top">
                    <p>2024 Copyright</p>
                </div>
                <div class="bottom">
                    <p>Twitter</p>
                    <p>Instagram</p>
                </div>
            </div>
            
        </div>
    </nav>
</template>

<style lang="postcss">
    
    .linea-fina{
    opacity: 70%;
    height: 0.5px;
    width: 100%;
}
    .footer-container{
        display: flex;
        flex-direction: column;
        width: 100%;
        align-items: center;
    }
    .footer{
        display: flex;
        flex-direction: row;
        width: 85%;
        justify-content: space-between;
        gap: 100px;
        height: 280px;
        padding-top: 50px;
        padding-bottom: 50px;

        .left-footer{
            display: flex;
            flex-direction: column;
            text-align: end;
            justify-content: space-between;
        }

        .info-footer{
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }
    }
</style>