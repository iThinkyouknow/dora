<template>
    <div class="flex flex-col justify-center w-screen py-20 px-24 bg-image">
        <div class="max-w-[50%]">
            <h1 class="font- text-5xl">
                Where developers' dreams come true
            </h1>
            <p class="mt-4">
                Explore the world of innovation at DoraHacks, BUIDLs, continuous funding, grants, bounties, and hackathons.
            </p>
            <div class="mt-12 flex gap-6 h-12 w-4/5">
                <ButtonPrimary>
                    Submit BUIDL
                </ButtonPrimary>
                <ButtonGhost>
                    Explore BUIDL
                </ButtonGhost>
            </div>
        </div>
    </div>
</template>
<style scoped>
.bg-image {
    background-image: url("https://hackerlink-static-contents.s3.ap-southeast-1.amazonaws.com/homepage/banner.jpg");
    background-position: right;
    background-size: cover;
    background-repeat: no-repeat;
    background-position-x: 50%;
    background-position-y: center;


}
</style>