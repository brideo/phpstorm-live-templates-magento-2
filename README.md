#Magento 2 Live Templates for PHP Storm

For more information see [my site](http://www.brideo.co.uk/magento2/Magento-2-PHP-Storm-Live-Templates/)

To make my life easier during the transition to Magento 2 I have created a bunch of live templates.

These are very basic and I will be expanding on these, also it would be nice if the community include their live templates in this repo.

##Magento 2 Controller

Shortcode: `mcontroller`

    <?php
    
    namespace $NAMESPACE$\Controller\$ACTION$;
    
    use Magento\Framework\App\Action\Action;
    use Magento\Framework\App\Action\Context;
    use Magento\Framework\View\Result\PageFactory;
    
    class $CLASS$ extends Action
    {
    
        /**
         * @var PageFactory
         */
        protected $resultPageFactory;
    
        /**
         * @var Context
         */
        protected $context;
    
        /**
         * Finder constructor.
         *
         * @param Context     $context
         * @param PageFactory $resultPageFactory
         */
        public function __construct(
            Context $context,
            PageFactory $resultPageFactory
        ) {
            parent::__construct($context);
            $this->resultPageFactory = $resultPageFactory;
            $this->context = $context;
        }
    
        /**
         * Load the page defined in view/frontend/layout/samplenewpage_index_index.xml
         *
         * @return \Magento\Framework\View\Result\\Magento\Framework\View\Result\Page
         */
        public function execute()
        {
            return $this->resultPageFactory->create();
        }
    }


##Magento 2 Block

Shortcode: `mblock`

    <?php
    
    namespace $NAMESPACE$\Block;
    
    use Magento\Framework\View\Element\Template;
    use Magento\Framework\View\Element\Template\Context;
    
    class $CLASS$ extends Template
    {
    
        /**
         * Constructor
         *
         * @param Context $context
         * @param array   $data
         */
        public function __construct(
            Context $context,
            array $data = []$DEPENDENCY$
        ) {
            parent::__construct($context, $data);
        }
    }

##Magento 2 Di.xml

Shortcode: `mdi`

    <?xml version="1.0"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
        <preference for="$NAMESPACE$\Api\$CLASSNAME$Interface" type="$NAMESPACE$\Service\$CLASSNAME$" />
    </config>

##Magento 2 Basic layout.xml

Shortcode: `mlayout`

    <?xml version="1.0"?>
    <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" layout="1column" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
        <body>
            <referenceContainer name="content">
                <block class="$NAMESPACE$\$MODULE$\Block\$BLOCK$" name="$NAME$" template="$NAMESPACE$_$MODULE$::$TEMPLATE$.phtml" />
            </referenceContainer>
        </body>
    </page>

##Magento 2 `module.xml`

Shortcode: `mmodule`

    <?xml version="1.0"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
        <module name="$MODULE$" setup_version="1.0.0" />
    </config>

##Magento 2 `routes.xml`

Shortcode `mroutes`

    <?xml version="1.0"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/etc/routes.xsd">
        <router id="$AREA$">
            <route id="$FRONTNAME$" frontName="$FRONTNAME$">
                <module name="$MODULE$" />
            </route>
        </router>
    </config>

