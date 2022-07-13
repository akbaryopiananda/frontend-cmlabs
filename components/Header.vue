<template>
    <div>
        <b-navbar toggleable="lg" type="light" variant="light">
            <b-container>
                <b-navbar-brand href="/">mealapp</b-navbar-brand>

                <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

                <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav class="ml-auto">
                    <b-nav-item href="/" active right>Home</b-nav-item>
                    <b-nav-item href="/" right>Foods</b-nav-item>
                    <b-nav-item href="/" right>Ingredients</b-nav-item>
                    <b-nav-item href="/" right>Local Culinary</b-nav-item>
                </b-navbar-nav>
                </b-collapse>
            </b-container>
        </b-navbar>
    </div>
</template>