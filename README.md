        const mobileMenu = document.querySelector('.mobile-menu');
        const menuButton = document.querySelector('.flex button.md\\:hidden');
        const closeButton = document.querySelector('.close-menu');
        
        menuButton.addEventListener('click', function() {
            mobileMenu.classList.remove('hidden');
        });
        
        closeButton.addEventListener('click', function() {
            mobileMenu.classList.add('hidden');
        });
        
        // Simulate adding to cart
        const addToCartButtons = document.querySelectorAll('.cart-btn');
        addToCartButtons.forEach(button => {
            button.addEventListener('click', function(e) {
                e.preventDefault();
                const originalText = button.innerText;
                button.innerHTML = '<i class="fas fa-check mr-2"></i>Added';
                button.classList.add('bg-purple-600', 'text-white');
                button.classList.remove('text-purple-600');
                
                setTimeout(() => {
                    button.innerHTML = originalText;
                    button.classList.remove('bg-purple-600', 'text-white');
                    button.classList.add('text-purple-600');
                }, 2000);
            });
        });
    });
</script>
