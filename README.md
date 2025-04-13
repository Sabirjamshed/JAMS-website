import { useState, useEffect, useRef } from 'react';
import { ShoppingBag, Search, User, Heart, Menu, X, ArrowRight, ChevronRight, Instagram, Facebook, Linkedin, Youtube, MessageSquare } from 'lucide-react';

// Main App Component
export default function JAMSEcommerce() {
    const [isMenuOpen, setIsMenuOpen] = useState(false);
    const [currentSlide, setCurrentSlide] = useState(0);
    const [activeCategory, setActiveCategory] = useState('All');

    // Product categories data
    const categories = [
        'Wallets', 'Card Cases', 'Belts', 'Messenger Bags',
        'Laptop Bags', 'Purses', 'Metal Cases', 'Watch Straps', 'Accessories'
    ];

    // Slider data for homepage
    const sliderData = [
        {
            id: 1,
            image: "/api/placeholder/1200/600",
            title: "Premium Leather Wallets",
            subtitle: "Handcrafted Excellence"
        },
        {
            id: 2,
            image: "/api/placeholder/1200/600",
            title: "Elegant Card Cases",
            subtitle: "Minimalist Design"
        },
        {
            id: 3,
            image: "/api/placeholder/1200/600",
            title: "Luxurious Belts",
            subtitle: "Signature Collection"
        },
        {
            id: 4,
            image: "/api/placeholder/1200/600",
            title: "Designer Messenger Bags",
            subtitle: "Urban Sophistication"
        },
        {
            id: 5,
            image: "/api/placeholder/1200/600",
            title: "Executive Laptop Bags",
            subtitle: "Modern Professionals"
        },
        {
            id: 6,
            image: "/api/placeholder/1200/600",
            title: "Stylish Purses",
            subtitle: "Refined Elegance"
        },
        {
            id: 7,
            image: "/api/placeholder/1200/600",
            title: "Premium Metal Cases",
            subtitle: "Durability Meets Style"
        },
        {
            id: 8,
            image: "/api/placeholder/1200/600",
            title: "Artisanal Watch Straps",
            subtitle: "Timeless Craftsmanship"
        },
        {
            id: 9,
            image: "/api/placeholder/1200/600",
            title: "Curated Accessories",
            subtitle: "Complete Your Look"
        }
    ];

    // Blog posts data
    const blogPosts = [
        {
            id: 1,
            title: "The Art of Leather Craftsmanship",
            excerpt: "Discover the meticulous process behind our handcrafted leather goods...",
            image: "/api/placeholder/400/300",
            date: "April 2, 2025"
        },
        {
            id: 2,
            title: "Sustainable Luxury: Our Commitment",
            excerpt: "How JAMS® is leading the way in sustainable luxury manufacturing...",
            image: "/api/placeholder/400/300",
            date: "March 28, 2025"
        },
        {
            id: 3,
            title: "Style Guide: Matching Wallets with Outfits",
            excerpt: "Expert tips on pairing your premium wallet with different attires...",
            image: "/api/placeholder/400/300",
            date: "March 15, 2025"
        }
    ];

    // Featured products data with ₹ symbol
    const featuredProducts = [
        {
            id: 1,
            name: "Executive Bifold Wallet",
            category: "Wallets",
            price: "₹4,999",
            image: "/api/placeholder/300/300"
        },
        {
            id: 2,
            name: "Slim Card Holder",
            category: "Card Cases",
            price: "₹2,499",
            image: "/api/placeholder/300/300"
        },
        {
            id: 3,
            name: "Premium Leather Belt",
            category: "Belts",
            price: "₹3,999",
            image: "/api/placeholder/300/300"
        },
        {
            id: 4,
            name: "Urban Messenger Bag",
            category: "Messenger Bags",
            price: "₹7,999",
            image: "/api/placeholder/300/300"
        },
        {
            id: 5,
            name: "Professional Laptop Sleeve",
            category: "Laptop Bags",
            price: "₹6,499",
            image: "/api/placeholder/300/300"
        },
        {
            id: 6,
            name: "Designer Clutch Purse",
            category: "Purses",
            price: "₹5,299",
            image: "/api/placeholder/300/300"
        },
        {
            id: 7,
            name: "Business Card Case",
            category: "Metal Cases",
            price: "₹3,299",
            image: "/api/placeholder/300/300"
        },
        {
            id: 8,
            name: "Artisan Watch Band",
            category: "Watch Straps",
            price: "₹2,799",
            image: "/api/placeholder/300/300"
        },
        {
            id: 9,
            name: "Leather Keychain",
            category: "Accessories",
            price: "₹999",
            image: "/api/placeholder/300/300"
        }
    ];

    // Auto-rotate slider effect
    useEffect(() => {
        const interval = setInterval(() => {
            setCurrentSlide(prevSlide => (prevSlide + 1) % sliderData.length);
        }, 5000);

        return () => clearInterval(interval);
    }, [sliderData.length]);

    // Toggle mobile menu
    const toggleMenu = () => {
        setIsMenuOpen(!isMenuOpen);
    };

    return (
        <div className="flex flex-col min-h-screen bg-white">
            {/* Header */}
            <header className="sticky top-0 z-50 bg-white shadow-sm">
                <div className="container mx-auto px-4 py-4">
                    <div className="flex items-center justify-between">
                        {/* Logo */}
                        <div className="flex items-center">
                            <h1 className="text-3xl font-bold text-gray-900">JAMS<sup className="text-sm">®</sup></h1>
                        </div>

                        {/* Desktop Navigation */}
                        <nav className="hidden md:flex space-x-8">
                            {categories.map((category) => (
                                <button
                                    key={category}
                                    className={`text-sm font-medium transition-colors hover:text-gray-900 ${activeCategory === category ? 'text-gray-900 border-b-2 border-gray-900' : 'text-gray-600'
                                        }`}
                                    onClick={() => setActiveCategory(category)}
                                >
                                    {category}
                                </button>
                            ))}
                        </nav>

                        {/* Icons */}
                        <div className="flex items-center space-x-4">
                            <button className="text-gray-700 hover:text-gray-900 transition-colors">
                                <Search size={20} />
                            </button>
                            <button className="text-gray-700 hover:text-gray-900 transition-colors">
                                <User size={20} />
                            </button>
                            <button className="text-gray-700 hover:text-gray-900 transition-colors">
                                <Heart size={20} />
                            </button>
                            <button className="relative text-gray-700 hover:text-gray-900 transition-colors">
                                <ShoppingBag size={20} />
                                <span className="absolute -top-1 -right-1 bg-gray-900 text-white text-xs rounded-full h-4 w-4 flex items-center justify-center">
                                    0
                                </span>
                            </button>

                            {/* Mobile menu button */}
                            <button
                                className="md:hidden text-gray-700 hover:text-gray-900 transition-colors"
                                onClick={toggleMenu}
                            >
                                {isMenuOpen ? <X size={24} /> : <Menu size={24} />}
                            </button>
                        </div>
                    </div>
                </div>

                {/* Mobile Navigation */}
                {isMenuOpen && (
                    <div className="md:hidden bg-white border-t border-gray-100 py-4">
                        <div className="container mx-auto px-4">
                            <nav className="flex flex-col space-y-4">
                                {categories.map((category) => (
                                    <button
                                        key={category}
                                        className={`text-sm font-medium transition-colors hover:text-gray-900 ${activeCategory === category ? 'text-gray-900 font-semibold' : 'text-gray-600'
                                            }`}
                                        onClick={() => {
                                            setActiveCategory(category);
                                            setIsMenuOpen(false);
                                        }}
                                    >
                                        {category}
                                    </button>
                                ))}
                            </nav>
                        </div>
                    </div>
                )}
            </header>

            <main className="flex-grow">
                {/* Hero Slider */}
                <section className="relative overflow-hidden h-96 md:h-screen">
                    {sliderData.map((slide, index) => (
                        <div
                            key={slide.id}
                            className={`absolute inset-0 transition-opacity duration-1000 ease-in-out ${index === currentSlide ? 'opacity-100' : 'opacity-0'
                                }`}
                        >
                            <img
                                src={slide.image}
                                alt={slide.title}
                                className="object-cover w-full h-full"
                            />
                            <div className="absolute inset-0 bg-black bg-opacity-20 flex flex-col justify-center items-center text-white text-center px-4">
                                <h2 className="text-4xl md:text-6xl font-bold mb-4">{slide.title}</h2>
                                <p className="text-xl md:text-2xl mb-8">{slide.subtitle}</p>
                                <button className="bg-white text-gray-900 px-6 py-3 rounded-none hover:bg-gray-900 hover:text-white transition-colors flex items-center space-x-2">
                                    <span>Shop Now</span>
                                    <ArrowRight size={16} />
                                </button>
                            </div>
                        </div>
                    ))}
                </section>

                {/* Category Highlights */}
                <section className="py-16 bg-gray-50">
                    <div className="container mx-auto px-4">
                        <h2 className="text-3xl font-bold text-center mb-12">Explore Our Collections</h2>
                        <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
                            {categories.slice(0, 3).map((category) => (
                                <div
                                    key={category}
                                    className="group relative h-64 overflow-hidden cursor-pointer"
                                >
                                    <img
                                        src="/api/placeholder/400/400"
                                        alt={category}
                                        className="object-cover w-full h-full transform group-hover:scale-110 transition-transform duration-500"
                                    />
                                    <div className="absolute inset-0 bg-black bg-opacity-30 flex items-center justify-center">
                                        <h3 className="text-white text-2xl font-bold">{category}</h3>
                                    </div>
                                    <div className="absolute bottom-0 left-0 right-0 bg-white bg-opacity-90 py-3 px-4 transform translate-y-full group-hover:translate-y-0 transition-transform duration-300">
                                        <div className="flex justify-between items-center">
                                            <span className="text-gray-900 font-medium">View Collection</span>
                                            <ChevronRight size={20} className="text-gray-900" />
                                        </div>
                                    </div>
                                </div>
                            ))}
                        </div>

                        <div className="grid grid-cols-1 md:grid-cols-3 gap-8 mt-8">
                            {categories.slice(3, 6).map((category) => (
                                <div
                                    key={category}
                                    className="group relative h-64 overflow-hidden cursor-pointer"
                                >
                                    <img
                                        src="/api/placeholder/400/400"
                                        alt={category}
                                        className="object-cover w-full h-full transform group-hover:scale-110 transition-transform duration-500"
                                    />
                                    <div className="absolute inset-0 bg-black bg-opacity-30 flex items-center justify-center">
                                        <h3 className="text-white text-2xl font-bold">{category}</h3>
                                    </div>
                                    <div className="absolute bottom-0 left-0 right-0 bg-white bg-opacity-90 py-3 px-4 transform translate-y-full group-hover:translate-y-0 transition-transform duration-300">
                                        <div className="flex justify-between items-center">
                                            <span className="text-gray-900 font-medium">View Collection</span>
                                            <ChevronRight size={20} className="text-gray-900" />
                                        </div>
                                    </div>
                                </div>
                            ))}
                        </div>

                        <div className="grid grid-cols-1 md:grid-cols-3 gap-8 mt-8">
                            {categories.slice(6).map((category) => (
                                <div
                                    key={category}
                                    className="group relative h-64 overflow-hidden cursor-pointer"
                                >
                                    <img
                                        src="/api/placeholder/400/400"
                                        alt={category}
                                        className="object-cover w-full h-full transform group-hover:scale-110 transition-transform duration-500"
                                    />
                                    <div className="absolute inset-0 bg-black bg-opacity-30 flex items-center justify-center">
                                        <h3 className="text-white text-2xl font-bold">{category}</h3>
                                    </div>
                                    <div className="absolute bottom-0 left-0 right-0 bg-white bg-opacity-90 py-3 px-4 transform translate-y-full group-hover:translate-y-0 transition-transform duration-300">
                                        <div className="flex justify-between items-center">
                                            <span className="text-gray-900 font-medium">View Collection</span>
                                            <ChevronRight size={20} className="text-gray-900" />
                                        </div>
                                    </div>
                                </div>
                            ))}
                        </div>
                    </div>
                </section>

                {/* Featured Products */}
                <section className="py-16">
                    <div className="container mx-auto px-4">
                        <div className="flex justify-between items-center mb-12">
                            <h2 className="text-3xl font-bold">Featured Products</h2>
                            <button className="text-gray-900 border-b border-gray-900 pb-1 flex items-center space-x-2 hover:text-gray-600 hover:border-gray-600 transition-colors">
                                <span>View All</span>
                                <ArrowRight size={16} />
                            </button>
                        </div>

                        <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8">
                            {featuredProducts.slice(0, 8).map((product) => (
                                <div key={product.id} className="group">
                                    <div className="relative overflow-hidden mb-4">
                                        <img
                                            src={product.image}
                                            alt={product.name}
                                            className="w-full h-64 object-cover transform group-hover:scale-105 transition-transform duration-500"
                                        />
                                        <div className="absolute bottom-0 left-0 right-0 p-4 bg-white bg-opacity-90 transform translate-y-full group-hover:translate-y-0 transition-transform duration-300 flex justify-between">
                                            <button className="text-gray-900 hover:text-gray-600 transition-colors">
                                                <Heart size={20} />
                                            </button>
                                            <button className="bg-gray-900 text-white px-4 py-2 hover:bg-gray-700 transition-colors">
                                                Add to Cart
                                            </button>
                                        </div>
                                    </div>
                                    <h3 className="text-lg font-medium text-gray-900 mb-1">{product.name}</h3>
                                    <p className="text-gray-600 mb-2">{product.category}</p>
                                    <p className="text-lg font-bold text-gray-900">{product.price}</p>
                                </div>
                            ))}
                        </div>
                    </div>
                </section>

                {/* Blog Section */}
                <section className="py-16 bg-gray-50">
                    <div className="container mx-auto px-4">
                        <div className="flex justify-between items-center mb-12">
                            <h2 className="text-3xl font-bold">Latest From Our Blog</h2>
                            <button className="text-gray-900 border-b border-gray-900 pb-1 flex items-center space-x-2 hover:text-gray-600 hover:border-gray-600 transition-colors">
                                <span>View All Posts</span>
                                <ArrowRight size={16} />
                            </button>
                        </div>

                        <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
                            {blogPosts.map((post) => (
                                <div key={post.id} className="group">
                                    <div className="relative overflow-hidden mb-4">
                                        <img
                                            src={post.image}
                                            alt={post.title}
                                            className="w-full h-56 object-cover transform group-hover:scale-105 transition-transform duration-500"
                                        />
                                    </div>
                                    <h3 className="text-xl font-medium text-gray-900 mb-2">{post.title}</h3>
                                    <p className="text-gray-600 mb-4">{post.excerpt}</p>
                                    <div className="flex justify-between items-center">
                                        <span className="text-gray-600 text-sm">{post.date}</span>
                                        <button className="text-gray-900 hover:text-gray-600 transition-colors flex items-center space-x-2">
                                            <span>Read More</span>
                                            <ArrowRight size={16} />
                                        </button>
                                    </div>
                                </div>
                            ))}
                        </div>
                    </div>
                </section>
            </main>

            {/* Footer */}
            <footer className="bg-gray-900 text-white py-12">
                <div className="container mx-auto px-4">
                    <div className="grid grid-cols-1 md:grid-cols-3 gap-8">
                        {/* About Section */}
                        <div>
                            <h3 className="text-lg font-bold mb-4">About JAMS®</h3>
                            <p className="text-gray-400">JAMS® is dedicated to crafting premium leather goods and accessories. Explore our collections and experience timeless craftsmanship.</p>
                            <div className="flex space-x-4 mt-4">
                                <a href="#" className="text-gray-400 hover:text-white transition-colors"><Instagram size={20} /></a>
                                <a href="#" className="text-gray-400 hover:text-white transition-colors"><Facebook size={20} /></a>
                                <a href="#" className="text-gray-400 hover:text-white transition-colors"><Linkedin size={20} /></a>
                                <a href="#" className="text-gray-400 hover:text-white transition-colors"><Youtube size={20} /></a>
                            </div>
                        </div>

                        {/* Quick Links Section */}
                        <div>
                            <h3 className="text-lg font-bold mb-4">Quick Links</h3>
                            <ul className="space-y-2">
                                <li><a href="#" className="text-gray-400 hover:text-white transition-colors">Shop</a></li>
                                <li><a href="#" className="text-gray-400 hover:text-white transition-colors">About Us</a></li>
                                <li><a href="#" className="text-gray-400 hover:text-white transition-colors">Contact</a></li>
                                <li><a href="#" className="text-gray-400 hover:text-white transition-colors">Blog</a></li>
                            </ul>
                        </div>

                        {/* Contact Section */}
                        <div>
                            <h3 className="text-lg font-bold mb-4">Contact Us</h3>
                            <p className="text-gray-400 mb-2">Email: support@jams.com</p>
                            <p className="text-gray-400 mb-2">Phone: +91 9876543210</p>
                            <p className="text-gray-400">Address: 123, JAMS Avenue, City, Country</p>
                        </div>
                    </div>
                    <div className="text-center mt-8">
                        <p className="text-gray-400">© 2025 JAMS®. All rights reserved.</p>
                    </div>
                </div>
            </footer>
        </div>
    );
}
